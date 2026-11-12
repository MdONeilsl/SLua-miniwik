# local

The scope declaration keyword. Introduces a new variable or function binding whose visibility is limited to the enclosing block. Without `local`, an assignment creates or updates a global. With `local`, the binding lives only as long as its block and cannot be reached from outside that block. `local` is the single most important keyword in SLua for correctness, performance, and memory: it is the default that every variable should use unless there is a specific reason not to. This page lists every form `local` can take, the scoping rule that governs each, and the interaction with `const`, `function`, and `export`.

## Contents

- [Purpose](#purpose)
- [Declaring a local variable](#declaring-a-local-variable)
- [Declaring without an initialiser](#declaring-without-an-initialiser)
- [Multiple assignment](#multiple-assignment)
- [Local function declaration](#local-function-declaration)
- [Local const declaration](#local-const-declaration)
- [Exported local declaration](#exported-local-declaration)
- [Scope rules](#scope-rules)
- [Shadowing](#shadowing)
- [Captured locals and closures](#captured-locals-and-closures)
- [Locals inside loop bodies](#locals-inside-loop-bodies)
- [Performance and memory](#performance-and-memory)
- [Interaction with globals](#interaction-with-globals)
- [Restrictions](#restrictions)

## Purpose

`local` binds a name to a value in the current block. The binding is visible from the line of declaration to the matching `end` of that block, and nowhere else. Locals live on the stack and are released when the block ends; globals live in a shared environment table and persist for the lifetime of the script.

```lua
local x = 1

local function show(): ()
    local y = 2
    print(x, y)        -- 1  2
end

show()
-- print(y)            -- compile error: y is out of scope
```

**Breakdown**

- `local x = 1` binds `x` in the enclosing block.
- `local y = 2` binds `y` only inside `show`.
- `print(x, y)` reads both; `x` is captured from the outer scope, `y` is local.
- After `show` returns, `y` no longer exists.

## Declaring a local variable

The basic form: `local name = expression`. The name is bound to the value of the expression, and the binding is visible from that line onward inside the enclosing block.

```lua
local count = 0
local name = "player"
local items = { "sword", "shield" }
```

**Breakdown**

- `local count = 0` binds `count` to `0` in the current block.
- `local name = "player"` binds `name` to the string `"player"`.
- `local items = { ... }` binds `items` to a table value.
- All three names are visible in the rest of the block and not outside it.

## Declaring without an initialiser

The initialiser is optional. A local declared without one is initialised to `nil`, and can be assigned later.

```lua
local result

if condition then
    result = computeValue()
end

print(result)
```

**Breakdown**

- `local result` declares the binding with value `nil`.
- The `if` block may assign to `result` or leave it as `nil`.
- `print(result)` reads the final value, which is `nil` if the `if` did not assign.
- Declaring first and assigning later is the standard pattern when the value depends on a condition.

## Multiple assignment

One `local` can declare several variables at once. The expressions on the right are evaluated first, then assigned left to right. Extra values on the right are discarded; missing values become `nil`.

```lua
local a, b, c = 1, 2, 3
local x, y = computeXY()
local p, q = 1
```

**Breakdown**

- `local a, b, c = 1, 2, 3` binds three variables in one declaration.
- `local x, y = computeXY()` captures both returns of the call.
- `local p, q = 1` binds `p` to `1` and `q` to `nil` because only one value was supplied.
- Swap without a temporary: `a, b = b, a` reassigns both bindings in one step.

## Local function declaration

`local function name(...) ... end` binds the function name **before** the body is compiled. This is the form that enables recursion and mutual references between locals.

```lua
local function factorial(n: number): number
    if n <= 1 then return 1 end
    return n * factorial(n - 1)
end
```

**Breakdown**

- `local function factorial(...)` declares `factorial` as a local and makes it visible inside its own body.
- The recursive call `factorial(n - 1)` resolves to the same function.
- `local factorial = function(...)` would not work for recursion because the name is not visible inside the body.

## Local const declaration

`local const name = value` binds a constant that cannot be reassigned. The binding rules and scope are the same as `local`, but any assignment after the declaration is a compile error.

```lua
local const MAX_HP = 100
local const GREETING: string = "hello"
```

**Breakdown**

- `local const MAX_HP = 100` binds `MAX_HP` as an immutable local.
- `local const GREETING: string = "hello"` combines `const` with an explicit type.
- Reassigning either name later is a compile error.
- `const` requires an initialiser; `local const x` without a value is rejected.

## Exported local declaration

`export local name = value` at the top level of a module marks the local for inclusion in the module's export table, making it visible to importers as `Module.name`. The binding is still local to the module; the export makes a copy of the reference available outside.

```lua
export local version = "1.0"
export local settings = { debug = false }
```

**Breakdown**

- `export local version = "1.0"` exports the value `"1.0"` as `Module.version`.
- `export local settings = { ... }` exports a table by reference; changes inside the module are visible to importers.
- `export local` is only valid at the top level of a module; inside a function or block it is a compile error.

## Scope rules

A local is visible from the line of declaration to the end of the enclosing block. Blocks are opened by `do`, `if`, `for`, `while`, `repeat`, and `function`. Nested blocks can read and shadow outer locals, but outer blocks cannot see inner locals.

```lua
local outer = 1

do
    local inner = 2
    print(outer, inner)     -- 1  2
end

print(outer)                -- 1
-- print(inner)             -- compile error: inner is out of scope
```

**Breakdown**

- `outer` is visible in the outer block and in the `do` block.
- `inner` is visible only inside the `do` block.
- After the `do` block, `inner` no longer exists; referencing it is a compile error.

## Shadowing

A local may declare a name that is already in scope. The new declaration shadows the outer one for the rest of its block. The outer binding is unchanged and is visible again after the inner block ends.

```lua
local x = 1

do
    local x = 2
    print(x)       -- 2
end

print(x)           -- 1
```

**Breakdown**

- The inner `local x = 2` creates a new binding that shadows the outer `x` for the `do` block.
- Inside the block, `print(x)` sees the inner binding (`2`).
- After the block, `print(x)` sees the outer binding again (`1`).
- Shadowing is legal; use it to avoid leaks, but avoid it when the name is the same and the intent is unclear.

## Captured locals and closures

A local remains alive as long as any closure created in its scope references it. The closure captures the binding, not the value; later assignments to the local are visible to the closure.

```lua
local function counter()
    local n = 0
    return function(): number
        n += 1
        return n
    end
end

local next = counter()
print(next())      -- 1
print(next())      -- 2
```

**Breakdown**

- `local n = 0` is a local inside `counter`.
- The returned function captures `n`.
- After `counter` returns, `n` survives because the closure holds a reference.
- Each call to `next` mutates the captured `n` and returns its new value.

## Locals inside loop bodies

A local declared inside a loop body is created fresh on each iteration. Closures created inside the loop capture separate bindings, one per iteration.

```lua
local funcs = {}

for i = 1, 3 do
    local n = i
    funcs[i] = function(): number
        return n
    end
end

print(funcs[1]())    -- 1
print(funcs[2]())    -- 2
print(funcs[3]())    -- 3
```

**Breakdown**

- `local n = i` creates a distinct `n` on each iteration.
- Each closure captures its own `n`.
- Without `local n = i`, all three closures would share the loop variable `i`, which ends at `3`.
- The idiom `local copy = loopVar` before a closure is the standard fix for the "all closures see the last value" bug.

## Performance and memory

Locals are faster than globals: reads and writes compile to indexed stack access rather than table lookup. Locals are also released when the block ends, so keeping large temporaries in a `do ... end` block reduces peak memory.

```lua
do
    local big = buildLargeTable()
    use(big)
end
-- big is out of scope; the table can be collected
```

**Breakdown**

- `big` is a local in the `do` block.
- After `end`, the binding goes out of scope.
- The table becomes eligible for garbage collection once no other reference exists.
- Referencing `big` after the block is a compile error.

## Interaction with globals

Without `local`, an assignment writes to the global environment table. A read of an undeclared name also consults the global table. In a new script, the global table contains only the standard library names and the script's own assignments.

```lua
local count = 0        -- local
count = count + 1      -- writes the local

counter = 0            -- global, if not already a local
counter = counter + 1  -- reads and writes the global
```

**Breakdown**

- `local count = 0` binds `count` as a local; subsequent `count = ...` writes the local.
- `counter = 0` with no `local` writes the global `counter`.
- Access to globals is slower than access to locals.
- Under strict mode, reading an undeclared global may be reported as a type error.

## Restrictions

`local` must be followed by at least one name. A `local` inside a block cannot leak past the block's `end`. Redeclaring the same name with `local` in the same block is a compile error; redeclaring in a nested block is shadowing and is allowed.

```lua
-- local          -- compile error: missing name
-- local x, y     -- valid: both bound to nil
-- local x = 1
-- local x = 2    -- compile error: duplicate name in same block

do
    local x = 2   -- valid: shadowing in a nested block
end
```

**Breakdown**

- `local` alone is a syntax error; it needs at least one name.
- `local x, y` with no initialisers is valid; both names are `nil`.
- Two `local x` declarations in the same block are rejected.
- A `local x` in a nested block shadows the outer `x` and is allowed.

