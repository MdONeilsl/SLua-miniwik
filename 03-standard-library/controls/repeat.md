# repeat

The post-test loop statement. Repeatedly runs a block until its condition becomes truthy. Unlike `while`, which checks the condition before the first iteration, `repeat` checks the condition after the body, so the body always runs at least once. The loop opens with `repeat`, closes with `until cond`, and does not use `do` or `end`. This page lists every form the statement can take, the scoping rule for locals declared inside the body, and the interaction with `break` and `continue`.

## Contents

- [Purpose](#purpose)
- [Basic form](#basic-form)
- [Body runs at least once](#body-runs-at-least-once)
- [Locals in the until condition](#locals-in-the-until-condition)
- [repeat versus while](#repeat-versus-while)
- [Nested repeat loops](#nested-repeat-loops)
- [break inside repeat](#break-inside-repeat)
- [continue inside repeat](#continue-inside-repeat)
- [No do, no end](#no-do-no-end)
- [Restrictions](#restrictions)

## Purpose

`repeat` runs a block repeatedly, checking the loop condition after each pass. It exits when the condition is truthy. It is the correct choice when the body must run at least once, or when the exit condition depends on values computed inside the body.

```lua
local n = 0
repeat
    n += 1
until n >= 3

print(n)    -- 3
```

**Breakdown**

- `repeat` opens the loop body.
- `n += 1` runs, then `until n >= 3` is evaluated.
- The loop stops once `n >= 3` is true.
- `n` ends at `3`.

## Basic form

The syntax is `repeat body until condition`. `repeat` and `until` are paired; everything between them is the body. There is no `do`, no `then`, and no `end`.

```lua
local input = "quit"
repeat
    print("waiting")
until input == "quit"
```

**Breakdown**

- `repeat` opens the body.
- `print("waiting")` runs on every iteration.
- `until input == "quit"` closes the loop when `input` is `"quit"`.
- In this example the body runs exactly once because `input` is already `"quit"` on entry.

## Body runs at least once

Because the condition is evaluated after the body, the body always executes at least one time. This is the distinguishing property of `repeat` and the reason to choose it over `while`.

```lua
local done = true

repeat
    print("runs even though done is true")
until done
```

**Breakdown**

- `done` is `true` before the loop begins.
- `print("runs even though done is true")` still runs because the body precedes the condition check.
- `until done` then exits the loop.
- A `while done do ... end` would have skipped the body entirely.

## Locals in the until condition

A local declared inside the body is in scope inside the `until` condition. This is the only form in which a loop condition can reference a value that does not exist outside the loop, and it is a common reason to prefer `repeat` over `while`.

```lua
repeat
    local response = fetchResponse()
until response ~= nil
```

**Breakdown**

- `local response = fetchResponse()` is declared inside the body.
- `until response ~= nil` reads `response` from the body's scope.
- The loop exits when `fetchResponse()` returns a non-nil value.
- `response` is not visible after `until`; it goes out of scope with the loop.

## repeat versus while

The choice between `repeat` and `while` is a choice about when the condition is evaluated. Use `repeat` when the body must run at least once or when the condition depends on a body-local value; use `while` when the condition is known before the body runs and the body should be skipped entirely if it is false on entry.

```lua
local n = 5

repeat
    n -= 1
until n == 0

local m = 5
while m > 0 do
    m -= 1
end
```

**Breakdown**

- The `repeat` version runs the body, decrements `n`, and then checks the condition.
- The `while` version checks `m > 0`, runs the body, and repeats.
- Both end with the counter at `0` in this example.
- With `n = 0` on entry, the `repeat` version would still run the body once and set `n` to `-1`, while the `while` version would skip the body.

## Nested repeat loops

`repeat` loops nest to any depth. Each `until` closes the nearest unclosed `repeat`. The body of an outer `repeat` may contain an inner `repeat` with its own `until`.

```lua
local rows = 2
local cols = 2

local r = 0
repeat
    r += 1
    local c = 0
    repeat
        c += 1
        print(r, c)
    until c >= cols
until r >= rows
```

**Breakdown**

- The first `until c >= cols` closes the inner loop.
- The second `until r >= rows` closes the outer loop.
- The output pairs are `1 1`, `1 2`, `2 1`, `2 2`.
- Each loop has exactly one `until`; adding an extra `until` or an `end` is a syntax error.

## break inside repeat

`break` exits the innermost `repeat` loop immediately. The `until` condition is not evaluated on the iteration that ran `break`.

```lua
local n = 0
repeat
    n += 1
    if n == 3 then
        break
    end
until n >= 10

print(n)    -- 3
```

**Breakdown**

- The loop would run until `n >= 10`.
- At `n == 3`, `break` exits before `until n >= 10` is evaluated.
- `n` remains `3`.
- `break` after `until` is a compile error; it must be inside the body.

## continue inside repeat

`continue` skips the rest of the current iteration and jumps to the `until` condition. The condition is still evaluated, so the loop can exit on the iteration that ran `continue`.

```lua
local n = 0
repeat
    n += 1
    if n % 2 == 0 then
        continue
    end
    print(n)
until n >= 5
```

**Breakdown**

- `n += 1` runs first, then the `if` check.
- On even `n`, `continue` jumps to `until n >= 5`.
- On odd `n`, `print(n)` runs.
- The condition is evaluated on every iteration, including those that ran `continue`.

## No do, no end

`repeat` does not use `do` to open the body and does not use `end` to close it. `repeat` opens, `until` closes. Adding either is a syntax error and a common pitfall when converting from `while`.

```lua
-- repeat do ... until cond      -- compile error
-- repeat ... until cond end     -- compile error
```

**Breakdown**

- `repeat do` is rejected; the parser expects a statement after `repeat`, not `do`.
- `repeat ... until cond end` is rejected; the parser expects the next statement after `until`, not an extra `end`.
- The body of `repeat` is opened only by `repeat` and closed only by `until`.

## Restrictions

`repeat` must be followed by at least one statement and closed by `until cond`. An empty body or a missing `until` is a syntax error. `until` requires an expression; `repeat ... until` with no condition is rejected.

```lua
-- repeat until true            -- compile error: empty body
-- repeat print("x")            -- compile error: missing until
-- repeat print("x") until      -- compile error: missing condition
```

**Breakdown**

- `repeat until true` is rejected because the body is empty; use `do ... end` for a body that does not repeat.
- `repeat` without `until` is rejected at the end of the enclosing block.
- `until` with no expression is rejected; the condition must be present.
