# or

The logical disjunction operator. Combines two expressions into one: the result is the first operand if that operand is truthy, otherwise the second operand. `or` short-circuits, meaning that when the first operand is truthy, the second operand is not evaluated at all. This page lists every context in which `or` can appear, what it returns in each, and how it interacts with `and`, `not`, and the default-value idiom.

## Contents

- [Purpose](#purpose)
- [Short-circuit evaluation](#short-circuit-evaluation)
- [Return value: operand, not boolean](#return-value-operand-not-boolean)
- [Use in conditions](#use-in-conditions)
- [Chaining](#chaining)
- [Precedence with and and not](#precedence-with-and-and-not)
- [The default-value idiom](#the-default-value-idiom)
- [Guarded fallback chains](#guarded-fallback-chains)
- [Restrictions](#restrictions)

## Purpose

`or` is one of the three logical operators of SLua, together with `and` and `not`. Its purpose is to combine two expressions such that the result is truthy when either operand is truthy. It is used primarily to build compound conditions and to supply default values when the left operand is falsy. Like `and`, it returns one of its operands rather than a coerced boolean.

```lua
local a = true or true           -- true
local b = true or false          -- true
local c = false or true          -- true
local d = false or false         -- false
```

**Breakdown**

- `true or true` returns the first operand, `true`.
- `true or false` returns the first operand, `true`, without evaluating the right-hand side.
- `false or true` returns the second operand, `true`.
- `false or false` returns the second operand, `false`.

## Short-circuit evaluation

`or` evaluates its left operand first. If the left operand is truthy, the whole expression is that operand, and the right operand is never executed. If the left operand is falsy, the right operand is evaluated and its value is returned. This ordering is guaranteed and is relied on for supplying fallback values only when the primary value is missing.

```lua
local cached = nil
local value = cached or computeValue()
print(value)                 -- the result of computeValue()

local hit = 42
local other = hit or computeValue()
print(other)                 -- 42, computeValue is not called
```

**Breakdown**

- `cached or computeValue()` evaluates `computeValue()` because `cached` is `nil`.
- `hit or computeValue()` returns `hit` directly; `computeValue()` is never executed.
- The pattern is the basis for memoisation and lazy initialisation.

## Return value: operand, not boolean

The result of `or` is one of its two operands, not a coerced boolean. When the left operand is truthy, the result is that operand in its original type. When the left operand is falsy, the result is the second operand.

```lua
local a = "first" or "second"    -- "first"
local b = nil or 42              -- 42
local c = 0 or 99                -- 0
local d = false or "unused"      -- "unused"
```

**Breakdown**

- `"first" or "second"` returns `"first"` because the left operand is truthy.
- `nil or 42` returns `42` because `nil` is falsy.
- `0 or 99` returns `0` because `0` is truthy in SLua.
- `false or "unused"` returns `"unused"` because `false` is falsy.

## Use in conditions

`or` is often used inside the condition of `if`, `elseif`, `while`, and `repeat ... until` to allow any of several sub-conditions to hold. Because the result of `or` is truthy whenever either operand is truthy, it fits directly into any condition slot.

```lua
local isAdmin = false
local isOwner = true

if isAdmin or isOwner then
    print("access granted")
end
```

**Breakdown**

- `if isAdmin or isOwner then` enters the branch when either is truthy.
- Here `isOwner` is true, so the branch runs even though `isAdmin` is false.
- The same construction works inside `while`, `elseif`, and `until`.

## Chaining

`or` associates to the left. A chain of `or` returns the first truthy operand, or the last operand if every operand is falsy. Each operand is evaluated in order until a truthy one is found.

```lua
local a = nil or false or "found" or "unused"    -- "found"
local b = nil or false or nil                    -- nil
local c = "first" or "second" or "third"         -- "first"
```

**Breakdown**

- `nil or false or "found" or "unused"` stops at `"found"` and returns it; `"unused"` is not evaluated.
- `nil or false or nil` evaluates all three operands and returns the last one, `nil`.
- `"first" or "second" or "third"` returns `"first"` immediately; the rest are not evaluated.

## Precedence with and and not

`not` binds tighter than `and`, and `and` binds tighter than `or`. When mixing the three operators, `or` groups last. To override the default grouping, wrap the expression in parentheses.

```lua
local a = true or false and false         -- true
local b = (true or false) and false       -- false
local c = not false or false              -- true
```

**Breakdown**

- `true or false and false` parses as `true or (false and false)`, evaluating to `true`.
- `(true or false) and false` forces the `or` to evaluate first, producing `true and false`, which is `false`.
- `not false or false` parses as `(not false) or false`, evaluating to `true`.

## The default-value idiom

The pattern `x or default` is the standard way to supply a default when `x` may be `nil` or `false`. It works because `or` returns the left operand when it is truthy and the right operand otherwise.

```lua
local function greet(name: string?)
    local display = name or "guest"
    print("hello, " .. display)
end

greet(nil)          -- hello, guest
greet("alice")      -- hello, alice
```

**Breakdown**

- `name or "guest"` returns `name` when it is a non-empty string, and `"guest"` when `name` is `nil`.
- The idiom does not handle empty strings; `""` is truthy, so `"" or "guest"` returns `""`.
- To handle empty strings, add an explicit test: `#name > 0 and name or "guest"`.

## Guarded fallback chains

Chaining several `or` operands provides a fallback ladder: the first truthy operand wins. This is the standard replacement for nested `if` checks in expressions.

```lua
local user = { displayName = nil, username = "alice" }

local name = user.displayName or user.username or "anonymous"
print(name)         -- alice
```

**Breakdown**

- `user.displayName` is `nil`, so the first `or` falls through.
- `user.username` is `"alice"`, so the chain stops there.
- `"anonymous"` is never evaluated.
- If both fields were `nil`, the chain would return `"anonymous"`.

## Restrictions

`or` requires two operands. Writing `or` with one operand or with no operands is a syntax error. `or` cannot be used as a statement; it must appear as part of an expression.

```lua
-- or true             -- compile error: missing left operand
-- true or             -- compile error: missing right operand
-- true or false       -- valid as an expression, not as a statement
```

**Breakdown**

- `or true` is a syntax error because the left operand is missing.
- `true or` is a syntax error because the right operand is missing.
- `true or false` used on its own as a statement is rejected; wrap it in `local _ = ...` or use it inside a condition.

