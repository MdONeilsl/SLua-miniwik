# if

The conditional statement. Runs a block only when its condition is truthy, and optionally selects among alternate blocks with `elseif` and `else`. Every `if` chain begins with `if`, ends with `end`, and tests conditions from top to bottom, running the first branch whose condition is truthy. This page lists every form the statement can take, the truthiness rule that governs all conditions, and the interaction with `elseif`, `else`, and nested chains.

## Contents

- [Purpose](#purpose)
- [Single if](#single-if)
- [if with else](#if-with-else)
- [if with elseif](#if-with-elseif)
- [Full chain: if, elseif, else](#full-chain-if-elseif-else)
- [Truthiness](#truthiness)
- [Conditions with and and or](#conditions-with-and-and-or)
- [Nested if chains](#nested-if-chains)
- [Early return instead of else](#early-return-instead-of-else)
- [Type narrowing inside if](#type-narrowing-inside-if)
- [Restrictions](#restrictions)

## Purpose

`if` runs a block conditionally. It is the only statement in SLua that selects a branch at runtime. When the condition is truthy, the block runs; when it is falsy, the block is skipped and control moves to the next `elseif`, the `else`, or the `end`.

```lua
local ready = true

if ready then
    print("go")
end
```

**Breakdown**

- `if ready then` tests `ready`.
- Because `ready` is truthy, the body runs and prints `"go"`.
- If `ready` were `nil` or `false`, the body would be skipped.

## Single if

The simplest form: an `if` with only its condition and a body. The body runs when the condition is truthy and is skipped otherwise. No alternate branch exists.

```lua
local n = 5

if n > 0 then
    print("positive")
end
```

**Breakdown**

- `if n > 0 then` tests the comparison.
- For `n == 5`, the condition is true and `"positive"` is printed.
- For `n <= 0`, no branch runs; execution continues after `end`.

## if with else

Adding `else` supplies a default branch. Exactly one of the two branches runs: the `if` body when the condition is truthy, the `else` body when it is falsy.

```lua
local n = -2

if n > 0 then
    print("positive")
else
    print("not positive")
end
```

**Breakdown**

- For `n == -2`, the condition is false, so the `else` body runs and prints `"not positive"`.
- For `n > 0`, the `if` body runs and prints `"positive"`.
- There is no path in which neither branch runs.

## if with elseif

Adding one or more `elseif` branches tests extra conditions, each only if every earlier condition was falsy. The first truthy condition wins, and later conditions are not evaluated.

```lua
local score = 85

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
end
```

**Breakdown**

- The first condition `score >= 90` is false.
- The second condition `score >= 80` is true, so `"B"` is printed.
- If both were false, no branch would run because there is no `else`.

## Full chain: if, elseif, else

Combining `if`, one or more `elseif`, and a trailing `else` gives a chain in which exactly one branch always runs. The `else` catches every case not covered by the earlier conditions.

```lua
local score = 55

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
elseif score >= 70 then
    print("C")
else
    print("F")
end
```

**Breakdown**

- With `score == 55`, none of the `elseif` conditions match.
- The `else` branch runs and prints `"F"`.
- Exactly one branch runs regardless of the value of `score`.

## Truthiness

The condition of every `if` and `elseif` uses SLua truthiness: `nil` and `false` are falsy, and every other value is truthy, including `0`, `""`, empty tables, and empty strings. This differs from many other languages and is the source of most `if` bugs when porting code.

```lua
if 0 then print("runs") end
if "" then print("runs") end
if {} then print("runs") end
if nil then print("never") end
if false then print("never") end
```

**Breakdown**

- `0`, `""`, and `{}` are all truthy, so their bodies run.
- `nil` and `false` are falsy, so their bodies are skipped.
- To treat `0` or `""` as "absent", compare explicitly: `if n ~= 0 then ... end` or `if #s > 0 then ... end`.

## Conditions with and and or

The condition can be any expression, including compound expressions built with `and`, `or`, and `not`. The result of the expression is evaluated under the same truthiness rule.

```lua
local user = { name = "alice", admin = true }

if user and user.admin then
    print("admin panel")
end

if user.name == "alice" or user.name == "bob" then
    print("known user")
end
```

**Breakdown**

- `user and user.admin` is truthy because both parts are truthy; the first `if` body runs.
- `user.name == "alice" or user.name == "bob"` is truthy because the first side matches.
- `and` and `or` short-circuit; the right side is not evaluated when the left already determines the result.

## Nested if chains

An `if` statement may appear inside the body of another `if`. Each nested statement is an independent chain with its own `end`. Nesting is allowed to any depth, though deeply nested chains are usually clearer when rewritten as early `return`s inside a function or as `elseif` chains.

```lua
local a = true
local b = false

if a then
    if b then
        print("both")
    else
        print("a only")
    end
end
```

**Breakdown**

- The outer `if a then` controls whether the inner chain is even reached.
- The inner `if b then ... else ... end` runs only when `a` is truthy.
- With `a == true` and `b == false`, `"a only"` is printed.

## Early return instead of else

Inside a function, an early `return` in an `if` body replaces the need for an `else`. The rest of the function serves as the `else` branch, and the result is flatter and easier to read.

```lua
local function classify(n: number): string
    if n > 0 then return "positive" end
    if n < 0 then return "negative" end
    return "zero"
end
```

**Breakdown**

- Each `if` returns immediately when its condition matches.
- The final `return "zero"` acts as the default branch; it runs only if neither earlier condition returned.
- This produces the same result as an `if ... elseif ... else` chain, with less indentation.

## Type narrowing inside if

Under strict mode, `if` narrows types inside its body. A test such as `if x then` narrows an optional type to its non-nil form, and a discriminant test such as `if x.kind == "circle" then` narrows a union to the matching variant.

```lua
local function describe(value: string?): string
    if value then
        return "got: " .. value
    end
    return "got nothing"
end
```

**Breakdown**

- `value: string?` is optional.
- Inside the `if value then` body, `value` is narrowed to `string`.
- The `return "got: " .. value` is accepted by the type checker because `value` is no longer optional there.
- Outside the `if`, `value` remains `string?`.

## Restrictions

An `if` requires a `then` after the condition and an `end` after the last branch. Omitting either is a syntax error. The condition must be an expression; a bare `if then` with no expression is rejected. Inside a single chain there may be exactly one `if`, any number of `elseif`, and at most one `else`, in that order.

```lua
-- if true              -- compile error: missing then
-- then print("x") end
-- if then print("x") end    -- compile error: missing condition
-- if a then end else end    -- compile error: else without if
```

**Breakdown**

- `if true then ... end` is required to have `then` on the same line or before the first statement of the body.
- A missing condition is rejected; use `if true then ... end` for an unconditional block, or use a `do ... end` block directly.
- An `else` without a preceding `if` in the same chain is rejected.
- More than one `else` in the same chain is rejected; `else` must appear at most once and last.
