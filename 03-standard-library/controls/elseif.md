# elseif

The intermediate alternative in a conditional chain. Adds an extra condition to an `if` statement, tested only when the controlling `if` and every preceding `elseif` are falsy. The chain is tested top to bottom and the first truthy condition wins. `elseif` may appear any number of times, but only after the `if` and before any `else`. This page lists every position where `elseif` is valid, what runs in each case, and the restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [After a single if](#after-a-single-if)
- [Chained multiple elseif](#chained-multiple-elseif)
- [With a trailing else](#with-a-trailing-else)
- [Inside a function with early return](#inside-a-function-with-early-return)
- [Interaction with truthiness](#interaction-with-truthiness)
- [Ordering matters](#ordering-matters)
- [Restriction: must follow if or elseif](#restriction-must-follow-if-or-elseif)
- [Restriction: must precede else](#restriction-must-precede-else)

## Purpose

`elseif` provides additional branches in a conditional chain. Each `elseif` adds one more condition. When the chain is evaluated, the parser tests the conditions in order and stops at the first truthy one.

```lua
local score = 85

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
end
```

**Breakdown**

- If `score >= 90`, the `if` branch runs.
- Otherwise, if `score >= 80`, the `elseif` branch runs.
- With `score == 85`, the first condition is false and the second is true; `"B"` is printed.

## After a single if

The simplest use: one `if` and one `elseif`. The second branch runs only when the first condition is falsy and the second is truthy.

```lua
local flag = false
local alt = true

if flag then
    print("flag")
elseif alt then
    print("alt")
end
```

**Breakdown**

- `flag` is false, so the first branch is skipped.
- `alt` is true, so the `elseif` branch runs and `"alt"` is printed.
- If both were false, neither branch would run.

## Chained multiple elseif

Any number of `elseif` branches may follow a single `if`. They are tested in source order; the first truthy condition wins and no later condition is evaluated.

```lua
local score = 75

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
elseif score >= 70 then
    print("C")
elseif score >= 60 then
    print("D")
end
```

**Breakdown**

- With `score == 75`, the first two conditions are false.
- The third condition `score >= 70` is true, so `"C"` is printed.
- The fourth condition is never evaluated; the chain stops at the first match.

## With a trailing else

An `else` after the last `elseif` catches every case not covered by earlier conditions. The chain now has a guaranteed branch.

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

- With `score == 55`, no `elseif` matches.
- The trailing `else` runs and prints `"F"`.
- `else` is optional; without it, the chain would fall through silently in the no-match case.

## Inside a function with early return

Each `elseif` can be replaced by an early `return` inside its own `if`. The two forms are equivalent; the early-return form is flatter.

```lua
local function classify(score: number): string
    if score >= 90 then return "A" end
    if score >= 80 then return "B" end
    if score >= 70 then return "C" end
    return "F"
end
```

**Breakdown**

- Each `if` returns immediately on match, so no `elseif` is needed.
- The final `return "F"` plays the role of the trailing `else`.
- With `score == 75`, the first two conditions are false, the third is true, and `"C"` is returned.

## Interaction with truthiness

Each `elseif` condition is evaluated under the same truthiness rules as `if`: only `nil` and `false` are falsy, everything else is truthy. A chain may short-circuit at any branch whose value happens to be truthy, including `0` and `""`.

```lua
local code = 0

if code == 1 then
    print("one")
elseif code then
    print("any non-nil code")
end
```

**Breakdown**

- `code == 1` is false for `code == 0`.
- `code` itself is truthy because `0` is truthy in SLua.
- The `elseif` branch runs and prints `"any non-nil code"`.
- To test for `0` specifically, compare explicitly: `elseif code == 0 then ...`.

## Ordering matters

Conditions are tested in source order. When conditions overlap, the first one that matches wins and later branches are not reached. Order them from most specific to least specific.

```lua
local x = 5

if x > 0 then
    print("positive")
elseif x > 3 then
    print("greater than three")
end
```

**Breakdown**

- `x == 5` satisfies both conditions.
- Because `x > 0` is tested first and is true, the `elseif` is never reached.
- The unreachable second branch is not an error, but it is dead code.
- To make the second branch meaningful, swap the order: `x > 3` first, then `x > 0`.

## Restriction: must follow if or elseif

`elseif` must appear after an `if` or another `elseif` in the same chain. A standalone `elseif` is a syntax error.

```lua
-- elseif x then    -- compile error: no matching if
--     print(x)
-- end
```

**Breakdown**

- `elseif` on its own has no controlling `if`.
- The parser rejects it before the chain begins.
- `elseif` is only meaningful as the second or later branch of an existing chain.

## Restriction: must precede else

`elseif` must come before any `else` in the chain. An `elseif` after `else` is a syntax error, because `else` already covers every remaining case.

```lua
if a then
    print("a")
else
    print("not a")
-- elseif b then     -- compile error: elseif after else
--     print("b")
end
```

**Breakdown**

- `else` ends the branch sequence.
- An `elseif` after `else` is rejected; the parser expects `end` next.
- All `elseif` branches must be written before the final `else`.
