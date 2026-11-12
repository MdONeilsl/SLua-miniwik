# `objects`

An object in SLua is a table with a metatable attached — there is no separate class or struct type. The metatable redirects field lookups, assignments, calls, and operators to user-supplied logic, which is how SLua's own classes (`LLEvents`, `LLTimers`, `PrimParamSetterType`) and any user-authored object are built.

## Contents

- [Attaching a metatable](#attaching-a-metatable)
- [Method lookup with `__index`](#method-lookup-with-__index)
- [Class-style pattern](#class-style-pattern)
- [Prototype-style pattern](#prototype-style-pattern)
- [Single inheritance](#single-inheritance)
- [Constructor chaining](#constructor-chaining)
- [Multiple inheritance](#multiple-inheritance)
- [Callable objects with `__call`](#callable-objects-with-__call)
- [Intercepting writes with `__newindex`](#intercepting-writes-with-__newindex)
- [Protecting the metatable](#protecting-the-metatable)
- [Operator metamethods](#operator-metamethods)

## Attaching a metatable
---
A table is created without a metatable. `setmetatable(t, mt)` installs one and returns `t`; `getmetatable(t)` retrieves it. A table carries at most one metatable, and the metatable is itself an ordinary table.

```lua
local point = { x = 3, y = 4 }
local mt = {}
setmetatable(point, mt)
print(getmetatable(point) == mt)  -- true
```

**Breakdown**

- `setmetatable(t, mt)` — installs `mt` as `t`'s metatable and returns `t`.
- `getmetatable(t)` — returns the installed metatable, or `nil` if none.

## Method lookup with `__index`
---
When a field read misses on a table, the VM consults the metatable's `__index` field. If it points at another table, that table is searched for the key; if it is a function, it is called with `(self, key)` and its return value is used.

```lua
local methods = {
    greet = function(self) return "hello, " .. self.name end,
}
local user = setmetatable({ name = "Ada" }, { __index = methods })
print(user:greet())  -- "hello, Ada"
```

**Breakdown**

- `{ __index = methods }` — a metatable whose `__index` points at the `methods` table.
- `user:greet()` — expands to `user.greet(user)`; `greet` is not on `user`, so `__index` reaches it through `methods`.

## Class-style pattern
---
The layout SLua's own classes use: a single table serves as both the method container and the metatable, and a `.new` function returns fresh instances.

```lua
local Counter = {}
Counter.__index = Counter

function Counter.new(start)
    return setmetatable({ count = start or 0 }, Counter)
end

function Counter:increment()
    self.count = self.count + 1
    return self.count
end

local c = Counter.new(5)
print(c:increment())  -- 6
```

**Breakdown**

- `Counter.__index = Counter` — instances look up missing keys on `Counter` itself; the table is simultaneously class, metatable, and method container.
- `Counter.new(start)` — constructor; `setmetatable({...}, Counter)` installs the dispatch for each instance.
- `Counter:increment()` — the `:` sugar passes the instance as `self`.

`PrimParamSetterType`, documented under `03-standard-library/classes/`, follows this shape: `PrimParamSetterType.new()` returns a fresh instance, and `:apply()` is resolved through `__index`. `LLEvents` and `LLTimers` use the same method-dispatch mechanism without a factory — each is a single pre-built instance.

## Prototype-style pattern
---
Instead of a `.new` function, instances inherit directly from a table used as a prototype.

```lua
local proto = {
    greet = function(self) return "hi, " .. self.name end,
}
local alice = setmetatable({ name = "Alice" }, { __index = proto })
local bob   = setmetatable({ name = "Bob" },   { __index = proto })
print(alice:greet(), bob:greet())  -- "hi, Alice"  "hi, Bob"
```

**Breakdown**

- `proto` — the fallback table; each instance's metatable points at it.
- No constructor; each instance is created inline with its own fields and shared method access.

## Single inheritance
---
A subclass is a table whose own metatable's `__index` points at the parent class. Lookups on the class itself (`Dog.speak`, `Dog.new`) fall back through this chain; lookups on an instance fall back through the instance's metatable, which is the subclass.

```lua
local Animal = {}
Animal.__index = Animal

function Animal.new(name)
    return setmetatable({ name = name }, Animal)
end

function Animal:speak()
    return self.name .. " makes a sound"
end

local Dog = setmetatable({}, { __index = Animal })
Dog.__index = Dog

function Dog.new(name)
    return setmetatable({ name = name }, Dog)
end

function Dog:speak()
    return self.name .. " barks"
end

local d = Dog.new("Rex")
print(d:speak())          -- "Rex barks"  (Dog.speak, override)
print(d.name)             -- "Rex"
print(Dog.new == Dog.new) -- true         (own method)
```

**Breakdown**

- `setmetatable({}, { __index = Animal })` — the class table `Dog` itself inherits from `Animal`, so `Dog` sees `Animal`'s methods even if `Dog` doesn't declare them.
- `Dog.__index = Dog` — instances route missing-key reads through `Dog` first, then (via `Dog`'s own metatable) through `Animal`.
- `Dog:speak()` — declares an override; because `Dog` has its own `speak`, the VM stops there and never reaches `Animal.speak`.

## Constructor chaining
---
A subclass constructor typically calls the parent constructor, then adds its own fields and re-installs the subclass metatable. Calling a parent *method* from an override uses the explicit `Parent.method(self, ...)` form, because `:` would rebind `self` incorrectly.

```lua
local Animal = {}
Animal.__index = Animal

function Animal.new(name)
    return setmetatable({ name = name }, Animal)
end

function Animal:describe()
    return "an animal named " .. self.name
end

local Dog = setmetatable({}, { __index = Animal })
Dog.__index = Dog

function Dog.new(name, breed)
    local self = Animal.new(name)      -- chain to parent constructor
    self.breed = breed
    return setmetatable(self, Dog)     -- re-target the metatable
end

function Dog:describe()
    return Animal.describe(self) .. " of breed " .. self.breed
end

local d = Dog.new("Rex", "corgi")
print(d:describe())  -- "an animal named Rex of breed corgi"
```

**Breakdown**

- `Animal.new(name)` — parent constructor runs first, giving `self` its base fields and the `Animal` metatable.
- `setmetatable(self, Dog)` — swaps the metatable from `Animal` to `Dog` so subsequent method lookups see `Dog`'s overrides. The `Animal` chain remains reachable via `Dog`'s own metatable.
- `Animal.describe(self)` — explicit parent call inside an override; `:` is not used because it would pass `Dog` as `self` and lose the parent dispatch.

Failing to call `setmetatable(self, Dog)` after `Animal.new` is a common bug — instances stay bound to the parent and never see `Dog`'s methods.

## Multiple inheritance
---
A class can inherit from more than one parent by installing an `__index` function on the class's own metatable. The function searches each parent in order until it finds the key.

```lua
local function createClass(...)
    local parents = { ... }
    local Class = {}
    setmetatable(Class, {
        __index = function(_, key)
            for i = 1, #parents do
                local v = parents[i][key]
                if v ~= nil then return v end
            end
        end,
    })
    Class.__index = Class
    return Class
end

local Swimmer = {}
Swimmer.__index = Swimmer
function Swimmer.new(name) return setmetatable({ name = name }, Swimmer) end
function Swimmer:swim() return self.name .. " swims" end

local Flyer = {}
Flyer.__index = Flyer
function Flyer.new(name) return setmetatable({ name = name }, Flyer) end
function Flyer:fly() return self.name .. " flies" end

local Duck = createClass(Swimmer, Flyer)
function Duck.new(name) return setmetatable({ name = name }, Duck) end
function Duck:quack() return self.name .. " quacks" end

local d = Duck.new("Donald")
print(d:swim())   -- "Donald swims"  (from Swimmer)
print(d:fly())    -- "Donald flies"  (from Flyer)
print(d:quack())  -- "Donald quacks" (own method)
```

**Breakdown**

- `createClass(Swimmer, Flyer)` — records both parents and installs a function-valued `__index` on the new class table.
- The `__index` function is only consulted when a lookup misses on `Duck` itself; it iterates parents in declaration order and returns the first hit.
- Order matters: if both parents define the same method, the leftmost wins. Swimmer's definition would shadow Flyer's.

An alternative is to copy parent methods into the subclass at definition time (`for k, v in pairs(Swimmer) do Duck[k] = v end`). Simpler, but methods added to a parent afterwards are not inherited — the function-based `__index` above is the version that stays live.

## Callable objects with `__call`
---
A table whose metatable carries `__call` can be invoked as if it were a function. The metamethod receives the table itself as the first argument, then whatever the caller passed.

```lua
local doubler = setmetatable({ factor = 2 }, {
    __call = function(self, x) return x * self.factor end,
})
print(doubler(21))  -- 42
```

**Breakdown**

- `__call` — receives `self` first, then the call arguments.
- `doubler(21)` — looks like a function call; the VM routes it to `__call` because the operand is a table.

## Intercepting writes with `__newindex`

`__newindex` is consulted when an assignment targets a key that is not yet present on the table. Assignments to existing keys bypass the metamethod and write directly. This is the standard mechanism for read-only views, validation, and logging.

```lua
local guard = setmetatable({ x = 1 }, {
    __newindex = function(self, k, v)
        error("write to '" .. tostring(k) .. "' is not allowed", 2)
    end,
})
guard.x = 2          -- default assignment, no error
guard.y = 1          -- error: write to 'y' is not allowed
```

**Breakdown**

- `__newindex` — called when the target key is missing from the table; the arriving key/value pair are its arguments.
- `guard.x = 2` — `x` exists, so the assignment is direct and `__newindex` does not fire.
- `error(..., 2)` — attributes the error to the caller rather than to the metamethod body.

## Protecting the metatable
---
If the current metatable carries a `__metatable` field, `setmetatable` on the same table raises an error, and `getmetatable` returns the `__metatable` value in place of the metatable itself.

```lua
local locked = setmetatable({}, { __metatable = "locked" })
print(getmetatable(locked))        -- "locked"
-- setmetatable(locked, {})        -- error: cannot change a protected metatable
```

**Breakdown**

- `__metatable` — any value; its presence marks the metatable read-only.
- `getmetatable(t)` — returns the `__metatable` value, not the metatable.

`table.freeze` is an alternative protection mechanism that blocks writes at the VM level instead of via a metamethod.

## Operator metamethods

The metamethods shown above (`__index`, `__call`, `__newindex`, `__metatable`) are the ones used to build objects. The VM also dispatches a further set to handle operators and protocols — `__add`, `__sub`, `__mul`, `__div`, `__mod`, `__pow`, `__unm`, `__eq`, `__lt`, `__le`, `__concat`, `__len`, `__iter`, `__mode`, `__tostring`, `__jsonhint`, `__tojson`. Each is documented, with its exact signature and argument contract, in [metamethods/](metamethods/).

The presence of any of these on a metatable changes how the VM handles the corresponding operation. Native values — numbers, strings, SLua's own `vector` and `quaternion` — carry their own native behavior and are not affected by a user-supplied `__add`, `__eq`, and so on. A metamethod only fires when at least one operand is a table (or userdata) that carries it.
