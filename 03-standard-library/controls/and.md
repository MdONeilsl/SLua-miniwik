## `and`

# and

The logical conjunction operator. Combines two expressions into one: the result is the first operand if that operand is falsy, otherwise the second operand. `and` short-circuits, meaning that when the first operand is falsy, the second operand is not evaluated at all. This page lists every context in which `and` can appear, what it returns in each, and how it interacts with the rest of the expression grammar.

## Purpose

`and` is one of the three logical operators of SLua, together with `or` and `not`. Its purpose is to combine two expressions such that the result is truthy only when both operands are truthy. It is used primarily to build compound conditions, but it also has a value-returning behavior that makes it useful outside conditions: the expression yields one of its operands, not a new boolean.

```lua
local a = true and true          -- true
local b = true and false         -- false
local c = false and true         -- false
local d = false and false        -- false
```

**Breakdown**

- `true and true` returns the second operand, `true`.
- `true and false` returns the second operand, `false`.
- `false and true` returns the first operand, `false`, without evaluating the right-hand side.
- `false and false` returns the first operand, `false`, without evaluating the right-hand side.

## Short-circuit evaluation

`and` evaluates its left operand first. If the left operand is falsy, the whole expression is that operand, and the right operand is never executed. If the left operand is truthy, the right operand is evaluated and its value is returned. This ordering is guaranteed and is relied on for guarding operations that would fail on an invalid left operand.

```lua
local user = nil
local name = user and user.name
print(name)                      -- nil

local count = 0
local ok = count > 0 and 10 / count
print(ok)                        -- false
```

**Breakdown**

- `user and user.name` returns `nil` without touching `user.name`, so no error is raised for indexing a nil value.
- `count > 0 and 10 / count` short-circuits on `count > 0` being false, so the division by zero is never attempted.
- Without short-circuiting, both right-hand expressions would raise.

## Return value: operand, not boolean

The result of `and` is one of its two operands, not a coerced boolean. When both operands are truthy, the result is the second operand in its original type. When the left operand is falsy, the result is that falsy value itself.

```lua
local a = 0 and "second"         -- "second"
local b = nil and 42             -- nil
local c = "first" and 7          -- 7
local d = false and "unused"     -- false
```

**Breakdown**

- `0 and "second"` returns `"second"` because `0` is truthy in SLua.
- `nil and 42` returns `nil` because `nil` is falsy; `42` is not evaluated.
- `"first" and 7` returns `7`, not `true`.
- `false and "unused"` returns `false`, not `"unused"`.

## Use in conditions

`and` is most often used inside the condition of `if`, `elseif`, `while`, and `repeat ... until` to require two or more sub-conditions to hold at the same time. Because the result of `and` is truthy exactly when both operands are truthy, it fits directly into any condition slot.

```lua
local hasKey = true
local hasPermission = false

if hasKey and hasPermission then
    print("granted")
else
    print("denied")
end
```

**Breakdown**

- `if hasKey and hasPermission then` enters the branch only when both are truthy.
- Here `hasPermission` is false, so the whole expression is false and the `else` branch runs.
- The same construction works inside `while`, `elseif`, and `until`.

## Chaining

`and` associates to the left. A chain of `and` returns the first falsy operand, or the last operand if every operand is truthy. Each operand is evaluated in order until a falsy one is found.

```lua
local a = true and 1 and "x" and {}       -- {}
local b = true and nil and "y"           -- nil
local c = false and 1 and 2              -- false
```

**Breakdown**

- `true and 1 and "x" and {}` evaluates each operand; since all are truthy, it returns the last one, `{}`.
- `true and nil and "y"` stops at `nil` and returns it; `"y"` is not evaluated.
- `false and 1 and 2` stops at `false` and returns it; neither `1` nor `2` is evaluated.

## Precedence with `or` and `not`

`not` binds tighter than `and`, and `and` binds tighter than `or`. When mixing the three operators in one expression, `and` groups first, then `or`.

```lua
local a = not true and false             -- false
local b = true and false or "fallback"   -- "fallback"
local c = false or true and "x"          -- "x"
```

**Breakdown**

- `not true and false` parses as `(not true) and false`, evaluating to `false`.
- `true and false or "fallback"` parses as `(true and false) or "fallback"`, evaluating to `"fallback"`.
- `false or true and "x"` parses as `false or (true and "x")`, evaluating to `"x"`.

## Combining with `or` for default values

The idiom `value and value.field` and its companion `value or default` are the standard SLua patterns for guarded access and default fallback. Together they cover the cases where a value might be missing and needs a safe default.

```lua
local config = { name = "alice" }

local name = config and config.name
local title = config and config.title or "guest"
```

**Breakdown**

- `config and config.name` returns `"alice"` because `config` is truthy and `config.name` is truthy.
- `config and config.title or "guest"` evaluates the `and` first; `config.title` is `nil`, so the `and` yields `nil`, and the `or` yields `"guest"`.
- If `config` itself were `nil`, both expressions would short-circuit to `nil` and `"guest"` respectively without raising.

## Type narrowing

Under strict mode, `and` narrows the type of its left operand when the right side requires it. After `x and x.field`, the compiler knows that inside the right side, `x` is non-nil.

```lua
local name: string? = getUserName()

if name and #name > 0 then
    print(name)
end
```

**Breakdown**

- `name: string?` is optional.
- `name and #name > 0` narrows `name` to `string` inside the right side.
- Inside the `if` body, `name` is treated as `string` by the type checker, not `string?`.
