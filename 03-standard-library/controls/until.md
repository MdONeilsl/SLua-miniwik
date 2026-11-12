# until

The `repeat` loop terminator and exit condition. Closes a `repeat` body and provides the expression that determines when the loop ends. `until` is paired with `repeat`; together they form the only post-test loop in SLua. `until` appears exactly once per `repeat` and never in any other construct. This page lists every position where `until` is valid, the scoping rule that makes it unique among loop conditions, and the restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [Basic form](#basic-form)
- [The condition is evaluated after the body](#the-condition-is-evaluated-after-the-body)
- [Locals in scope inside until](#locals-in-scope-inside-until)
- [Compound conditions](#compound-conditions)
- [Nested repeat loops](#nested-repeat-loops)
- [Interaction with break and continue](#interaction-with-break-and-continue)
- [until is not used in while or for](#until-is-not-used-in-while-or-for)
- [Restriction: exactly one until per repeat](#restriction-exactly-one-until-per-repeat)
- [Restriction: condition is mandatory](#restriction-condition-is-mandatory)

## Purpose

`until` closes a `repeat` loop and supplies the exit condition. The `repeat` keyword opens the body; the `until` keyword closes it and marks the point where the condition is checked. Control loops back to the statement after `repeat` if the condition is falsy, and continues after `until` if the condition is truthy.

```lua
local n = 0
repeat
    n += 1
until n >= 3
```

**Breakdown**

- `repeat` opens the body.
- `n += 1` runs, then `until n >= 3` is evaluated.
- The loop stops when `n >= 3` is true.
- Execution continues with the statement after `until`.

## Basic form

The syntax is `repeat body until condition`. The `until` follows the last statement of the body and is itself followed by the condition expression. There is no `then`, no `do`, and no `end`.

```lua
local input = ""
repeat
    input = fetchInput()
until input ~= ""
```

**Breakdown**

- `repeat` opens the body.
- `input = fetchInput()` runs on every iteration.
- `until input ~= ""` closes the loop when a non-empty input is received.
- The body runs at least once, so `fetchInput()` is always called once.

## The condition is evaluated after the body

`until` is checked **after** the body runs, not before. This is the key difference from `while`. The body always executes at least once, and the condition sees any changes the body made.

```lua
local done = true
repeat
    print("runs")
until done
```

**Breakdown**

- `done` is `true` before the loop begins.
- `print("runs")` still executes because the body precedes the condition check.
- `until done` then exits, but only after one pass.
- A `while done do ... end` would have skipped the body entirely.

## Locals in scope inside until

The `until` condition can read locals declared inside the body. No other loop in SLua allows this; `while` and `for` conditions are evaluated before the body's locals exist.

```lua
repeat
    local response = fetchResponse()
    process(response)
until response == nil
```

**Breakdown**

- `local response = fetchResponse()` is declared inside the body.
- `until response == nil` reads `response` from the body's scope.
- The loop exits when `fetchResponse()` returns `nil`.
- `response` goes out of scope at the end of the iteration; it is not visible after `until`.

## Compound conditions

The `until` condition may be any expression, including one built with `and`, `or`, and `not`. The loop exits when the entire expression is truthy.

```lua
local n = 0
local ok = true
repeat
    n += 1
    ok = check(n)
until n >= 10 or not ok
```

**Breakdown**

- The condition is `n >= 10 or not ok`.
- The loop exits when either `n >= 10` or `ok` is falsy.
- `and` and `or` short-circuit inside the condition, just as they do in an `if`.
- Wrapping the whole expression in parentheses does not change the exit rule.

## Nested repeat loops

`until` closes the nearest unclosed `repeat`. In nested `repeat` loops, each `until` closes its own loop; the outer `until` closes the outer loop.

```lua
local r = 0
repeat
    r += 1
    local c = 0
    repeat
        c += 1
    until c >= 2
until r >= 2
```

**Breakdown**

- The first `until c >= 2` closes the inner loop.
- The second `until r >= 2` closes the outer loop.
- Each `repeat` has exactly one `until`.
- The inner `until` is not visible to the outer loop.

## Interaction with break and continue

`break` inside the body exits the loop before `until` is evaluated. `continue` jumps directly to `until`; the condition is evaluated on the iteration that ran `continue`.

```lua
local n = 0
repeat
    n += 1
    if n == 5 then
        break
    end
until n >= 10
```

**Breakdown**

- At `n == 5`, `break` exits the loop before `until n >= 10` is evaluated.
- `n` remains `5`.
- `until` is only evaluated if the body runs to completion or to a `continue`.

## until is not used in while or for

`until` is exclusively the terminator of `repeat`. It is not used in `while`, `for`, `if`, or any other construct. The `while` loop uses `do` to open its body and `end` to close it; `for` does the same. Only `repeat` uses `until`.

```lua
-- while x do ... until cond     -- compile error: while does not use until
-- for i = 1, 3 do ... until x   -- compile error: for does not use until
-- if x then ... until cond      -- compile error: if does not use until
```

**Breakdown**

- `while` opens with `do` and closes with `end`.
- `for` opens with `do` and closes with `end`.
- `if` opens with `then` and closes with `end`.
- `until` belongs only to `repeat`.

## Restriction: exactly one until per repeat

Every `repeat` has exactly one matching `until`. Writing a second `until` in the same loop is a syntax error.

```lua
-- repeat
--     n += 1
-- until n >= 3
-- until n >= 5    -- compile error: second until in same loop
```

**Breakdown**

- The first `until` closes the loop.
- A second `until` in the same construct is rejected.
- To express multiple exit conditions, use `and` or `or` inside a single `until` condition.

## Restriction: condition is mandatory

`until` requires a condition expression. Writing `until` with no expression is a syntax error; the parser expects an expression after the keyword.

```lua
-- repeat
--     n += 1
-- until              -- compile error: missing condition
```

**Breakdown**

- `until` alone is rejected; the parser needs a condition.
- `until true` is valid and makes the loop run exactly once.
- `until false` is valid and makes the loop run forever unless `break` is used; avoid unless intentional.

