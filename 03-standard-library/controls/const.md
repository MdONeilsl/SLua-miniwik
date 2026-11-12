# const

The constant declaration modifier. Prefixed by `local`, it declares a binding that cannot be reassigned after initialisation. The restriction is enforced at compile time; there is no runtime check. `const` is a contextual keyword, valid in every position where `local` is valid, so introducing it does not break existing code. This page lists every context in which `local const` can appear, the rules that apply to each, and how it differs from freezing a table.

## Contents

- [Purpose](#purpose)
- [Top-level constants](#top-level-constants)
- [Inside a function body](#inside-a-function-body)
- [Inside a do block](#inside-a-do-block)
- [Inside a loop body](#inside-a-loop-body)
- [Const function declarations](#const-function-declarations)
- [Tables declared as const](#tables-declared-as-const)
- [Shadowing a const](#shadowing-a-const)
- [Difference from table.freeze](#difference-from-tablefreeze)
- [Restrictions](#restrictions)

## Purpose

`local const` marks a binding as immutable. It communicates intent, prevents accidental reassignment, and lets the compiler treat reads as invariant. A `const` binding is otherwise identical to a `local` binding: same scope rules, same visibility, same capture by closures.

```lua
local const MAX_HP = 100
local const GREETING: string = "hello"
```

**Breakdown**

- `local const MAX_HP = 100` declares a constant named `MAX_HP`.
- `local const GREETING: string = "hello"` combines `const` with an explicit annotation.
- Any later `MAX_HP = 200` or `GREETING = "bye"` is rejected by the compiler.

## Top-level constants

At the top level of a script, `local const` binds a constant that every handler in the file can read but no handler can reassign.

```lua
local const MAX_TOUCHES = 3
local const TIMEOUT = 5.0

LLEvents:on("touch_start", function(events)
    print(MAX_TOUCHES, TIMEOUT)
end)
```

**Breakdown**

- `MAX_TOUCHES` and `TIMEOUT` are visible inside the handler as upvalues.
- The handler reads both constants; neither can be assigned from inside the handler.
- An assignment such as `MAX_TOUCHES = 10` inside the handler is a compile error.

## Inside a function body

A `local const` inside a function is scoped to that function. Each call creates a fresh binding; there is no shared state between calls.

```lua
local function area(radius: number): number
    local const PI_APPROX = 3.14159
    return PI_APPROX * radius * radius
end
```

**Breakdown**

- `PI_APPROX` is recreated on every call to `area`.
- The function cannot reassign it; `PI_APPROX = 3.14` inside the body is rejected.
- The constant is not visible outside `area`.

## Inside a do block

A `local const` inside `do ... end` is scoped to the block. It is not visible after `end`.

```lua
do
    local const LOCAL_LIMIT = 10
    print(LOCAL_LIMIT)
end

-- print(LOCAL_LIMIT)    -- compile error
```

**Breakdown**

- `LOCAL_LIMIT` is visible inside the block.
- Outside the block, the binding no longer exists.
- Referencing it after `end` is a compile error, not a runtime `nil`.

## Inside a loop body

A `local const` inside a loop is recreated on every iteration. The constant-ness applies within each iteration, not across the loop.

```lua
for i = 1, 3 do
    local const index = i
    print(index)
end
```

**Breakdown**

- `index` is a new constant per iteration.
- Assigning to `index` inside the loop body is a compile error.
- Reading `index` after the loop is also a compile error because it is out of scope.

## Const function declarations

`const` may also introduce a function binding. The function value is created once and cannot be replaced, though the body still executes normally.

```lua
local const function double(n: number): number
    return n * 2
end
```

**Breakdown**

- `local const function double(...)` binds `double` as an immutable function value.
- Calling `double(5)` works exactly as with `local function`.
- Assigning `double = somethingElse` is rejected by the compiler.

## Tables declared as const

`local const` makes the binding immutable, not the table it holds. The table's fields can still be reassigned. This is the most common surprise with `const`.

```lua
local const config = { name = "alice", score = 0 }

config.score = 42           -- allowed
print(config.score)         -- 42

config = {}                 -- compile error
```

**Breakdown**

- `config.score = 42` mutates the table, not the binding; it is allowed.
- `config = {}` reassigns the binding, which is rejected.
- To make the table itself immutable, use `table.freeze(config)`.

## Shadowing a const

A `const` binding may be shadowed by a new declaration of the same name in an inner scope. The shadowing declaration is a separate binding with its own mutability.

```lua
local const x = 1

do
    local x = 2
    x = 3
    print(x)    -- 3
end

print(x)        -- 1
```

**Breakdown**

- The inner `local x = 2` shadows the outer `x`.
- The inner `x` is mutable; `x = 3` is allowed.
- The outer `x` is unchanged and still `1`.
- Shadowing a `const` with `local` is legal; the reverse, reassigning the `const` itself, is not.

## Difference from table.freeze

`local const` is a compile-time guarantee about the binding; `table.freeze` is a runtime guarantee about the table value. They solve different problems and are often combined.

```lua
local const LIMITS = table.freeze({ min = 0, max = 100 })

print(LIMITS.max)           -- 100
LIMITS.max = 200            -- runtime error: table is frozen
```

**Breakdown**

- `local const` prevents `LIMITS = ...`.
- `table.freeze` prevents `LIMITS.max = ...`.
- Together they make the value fully immutable for the lifetime of the script.
- `table.freeze` is shallow; nested tables must be frozen individually.

## Restrictions

`const` cannot be used without an initialiser. Every `const` binding must be assigned at the point of declaration.

```lua
local const x = 5           -- valid
-- local const y            -- compile error: missing initializer
-- local const z = nil      -- valid: explicit nil initializer
```

**Breakdown**

- `local const x = 5` is a valid constant declaration.
- `local const y` without an initialiser is rejected.
- `local const z = nil` is valid; the binding is const and holds `nil`.
- A `const` binding may hold any value; the restriction is on reassignment, not on the value itself.
