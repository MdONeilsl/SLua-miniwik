# not

The logical negation operator. Takes one operand and returns the opposite truthiness: `true` if the operand is falsy, `false` if the operand is truthy. `not` is the only unary logical operator in SLua and binds tighter than `and` and `or`. This page lists every context where `not` can appear, what it returns in each, and its precedence relative to the other logical operators.

## Contents

- [Purpose](#purpose)
- [Result is always a boolean](#result-is-always-a-boolean)
- [Use in conditions](#use-in-conditions)
- [Double negation](#double-negation)
- [Precedence with and and or](#precedence-with-and-and-or)
- [Negating comparisons](#negating-comparisons)
- [Negating membership tests](#negating-membership-tests)
- [Type narrowing](#type-narrowing)
- [Restrictions](#restrictions)

## Purpose

`not` inverts the truthiness of a single expression. Applied to a falsy value, it returns `true`; applied to a truthy value, it returns `false`. It does not coerce the operand, only its truthiness is inspected.

```lua
local a = not true          -- false
local b = not false         -- true
local c = not nil           -- true
local d = not 0             -- false
local e = not ""            -- false
```

**Breakdown**

- `not true` returns `false`.
- `not false` and `not nil` return `true`.
- `not 0` returns `false` because `0` is truthy in SLua.
- `not ""` returns `false` because the empty string is truthy.

## Result is always a boolean

Unlike `and` and `or`, which return one of their operands, `not` always returns an actual boolean. There is no case where `not x` evaluates to something other than `true` or `false`.

```lua
local x = "hello"
print(not x)                -- false
print(type(not x))          -- "boolean"

local y = 42
print(not y)                -- false
print(type(not y))          -- "boolean"
```

**Breakdown**

- `not "hello"` returns `false`, not the string `"hello"`.
- `not 42` returns `false`, not `42`.
- `type(not x)` is `"boolean"` for every value of `x`.

## Use in conditions

`not` is most often used inside the condition of `if`, `elseif`, `while`, and `repeat ... until` to invert a check. The result is a boolean and fits directly into any condition slot.

```lua
local connected = false

if not connected then
    print("offline")
end

while not done do
    step()
end
```

**Breakdown**

- `if not connected then` enters the branch when `connected` is falsy.
- `while not done do` repeats the body while `done` is falsy.
- The same pattern works with `elseif` and `until`.

## Double negation

`not not x` converts any value to its boolean equivalent: `true` if `x` is truthy, `false` if `x` is falsy. This is the standard way to force a value into a boolean when a boolean is required (for example, when a function is annotated to return `boolean`).

```lua
local value = 0
local flag = not not value       -- true
print(flag)

local nothing = nil
local other = not not nothing    -- false
print(other)
```

**Breakdown**

- `not not 0` evaluates `not 0` to `false`, then `not false` to `true`.
- `not not nil` evaluates to `false`.
- `not not x` is equivalent to a hypothetical `bool(x)` cast in other languages.
- Under strict mode, `not not x` narrows the type of `x` to `boolean`.

## Precedence with and and or

`not` binds tighter than `and` and `or`. In an expression that mixes the three operators, `not` groups first, then `and`, then `or`. To negate an entire compound expression, wrap it in parentheses.

```lua
local a = not true and false           -- false
local b = not (true and false)         -- true
local c = not true or false            -- false
local d = not (true or false)          -- false
```

**Breakdown**

- `not true and false` parses as `(not true) and false` and evaluates to `false`.
- `not (true and false)` negates the entire `and` expression and evaluates to `true`.
- `not true or false` parses as `(not true) or false` and evaluates to `false`.
- `not (true or false)` evaluates to `false`.
- Wrap the compound expression in parentheses to negate it as a unit.

## Negating comparisons

`not (a == b)` is equivalent to `a ~= b`, and `not (a ~= b)` is equivalent to `a == b`. Either form works; the `~=` and `==` forms are preferred for clarity.

```lua
local x, y = 1, 2

local neq1 = not (x == y)    -- true
local neq2 = x ~= y          -- true

local eq1 = not (x ~= y)     -- false
local eq2 = x == y           -- false
```

**Breakdown**

- `not (x == y)` returns `true` when `x` and `y` are different.
- `x ~= y` returns the same result without the negation.
- Use `~=` and `==` directly; use `not (a == b)` only when the comparison is itself part of a larger expression.

## Negating membership tests

`not (key in table)` is not a valid SLua expression; there is no `in` operator for membership outside of `for`. To test that a key is absent, compare the lookup directly with `nil` or wrap the check in `not`.

```lua
local config = { name = "alice" }

local missing1 = not config.title           -- true
local missing2 = config.title == nil         -- true
local missing3 = not (config.title ~= nil)   -- true
```

**Breakdown**

- `not config.title` returns `true` because `config.title` is `nil` and `nil` is falsy.
- `config.title == nil` returns the same result without the truthiness step.
- `not (config.title ~= nil)` is a double-negative form; the simpler comparison is preferred.

## Type narrowing

Under strict mode, `not` narrows types the same way a truthiness check does. A guard such as `if not x then return end` narrows `x` to its non-nil form on the statements after the guard.

```lua
local name: string? = getOptionalName()

if not name then
    return
end

print(#name)    -- name is string here, not string?
```

**Breakdown**

- `name: string?` is optional.
- Inside the `if not name then return end` guard, the `if` body handles the nil case.
- After the guard, `name` is narrowed to `string` by the type checker.
- The narrowing survives until the end of the enclosing block or a reassignment.

## Restrictions

`not` requires exactly one operand. Writing `not` with no operand or with two operands is a syntax error. `not` cannot be used as a statement; it must appear as part of an expression.

```lua
-- not            -- compile error: missing operand
-- not a, b       -- compile error: comma not allowed after not
-- not true       -- valid as an expression, not as a statement
```

**Breakdown**

- `not` alone is a syntax error; it needs an expression after it.
- `not a, b` is rejected; `not` takes a single operand.
- `not true` used on its own as a statement is rejected by the compiler; wrap it in `local _ = not true` or use it inside a condition.
