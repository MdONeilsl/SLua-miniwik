# while

The pre-test loop statement. Repeatedly runs a block while its condition stays truthy. The condition is evaluated before each iteration, including the first, so the body may run zero times if the condition is falsy on entry. `while` opens its body with `do` and closes it with `end`. This page lists every form the statement can take, the evaluation order of the condition, and the interaction with `break`, `continue`, and locals.

## Contents

- [Purpose](#purpose)
- [Basic form](#basic-form)
- [The condition is evaluated first](#the-condition-is-evaluated-first)
- [Body may run zero times](#body-may-run-zero-times)
- [Compound conditions](#compound-conditions)
- [Infinite loops](#infinite-loops)
- [Nested while loops](#nested-while-loops)
- [break inside while](#break-inside-while)
- [continue inside while](#continue-inside-while)
- [Locals inside the body](#locals-inside-the-body)
- [while versus repeat](#while-versus-repeat)
- [Restrictions](#restrictions)

## Purpose

`while` runs a block as long as a condition remains truthy. It is the correct choice when the number of iterations is not known in advance and the condition can be evaluated before the first pass. Each iteration re-evaluates the condition; the loop ends the first time the condition is falsy.

```lua
local n = 0
while n < 3 do
    n += 1
end

print(n)    -- 3
```

**Breakdown**

- `while n < 3 do` checks the condition before each pass.
- `n += 1` runs on each iteration.
- When `n` reaches `3`, the condition `n < 3` becomes false and the loop exits.
- `n` ends at `3`.

## Basic form

The syntax is `while condition do body end`. The condition follows the keyword directly; the body follows `do` and precedes `end`. The `do` is mandatory; omitting it is a syntax error.

```lua
local count = 10
while count > 0 do
    print(count)
    count -= 1
end
```

**Breakdown**

- `while count > 0 do` opens the loop and sets the condition.
- `print(count)` and `count -= 1` are the body.
- The body runs while `count > 0` remains true.
- `end` closes the loop; execution continues with the next statement after it.

## The condition is evaluated first

Unlike `repeat`, `while` checks the condition before the body. If the condition is falsy on entry, the body never runs. On each later iteration the condition is re-evaluated, so any change made by the body affects whether the loop continues.

```lua
local n = 5
while n < 3 do
    print("never")
end
```

**Breakdown**

- `n = 5` is not less than `3`.
- The condition is false on entry, so the body is skipped entirely.
- Execution continues after `end`.
- No `print` runs.

## Body may run zero times

Because the condition is checked first, a `while` loop may run its body zero times. This is the key difference from `repeat`, whose body always runs at least once. Use `while` when "do nothing" is a valid outcome; use `repeat` when the body must run at least once.

```lua
local queue = {}
while #queue > 0 do
    process(table.remove(queue))
end
```

**Breakdown**

- `#queue > 0` is false when the queue is empty.
- The body is skipped and nothing is processed.
- This is the correct behavior for an empty queue.
- If the queue had items, the loop would process them until it emptied.

## Compound conditions

The condition may be any expression, including one built with `and`, `or`, and `not`. The loop continues as long as the entire expression is truthy. All the usual short-circuit rules apply.

```lua
local n = 0
local ok = true
while n < 10 and ok do
    n += 1
    ok = check(n)
end
```

**Breakdown**

- The condition is `n < 10 and ok`.
- The loop continues while both parts are truthy.
- When `ok` becomes false, the loop exits even if `n < 10`.
- When `n >= 10`, the loop exits even if `ok` is still true.

## Infinite loops

A `while` with a condition that never becomes falsy runs forever. `while true do` is the idiomatic form for a loop intended to run until an internal `break` or `return`. Such loops must contain an exit path, or they will hang the script.

```lua
while true do
    local event = poll()
    if event == "quit" then
        break
    end
    handle(event)
end
```

**Breakdown**

- `while true do` is always truthy, so the loop has no condition-based exit.
- The `break` inside is the only way to leave the loop.
- Without a `break` or `return`, this loop never ends.
- The engine eventually times out the script; do not rely on that for correctness.

## Nested while loops

`while` loops nest to any depth. Each `while` opens its own body with `do` and closes it with `end`. An inner `while` closes at its own `end`; the outer `while` continues until its own condition is falsy.

```lua
local r = 0
while r < 2 do
    r += 1
    local c = 0
    while c < 2 do
        c += 1
        print(r, c)
    end
end
```

**Breakdown**

- The first `end` closes the inner `while`.
- The second `end` closes the outer `while`.
- Output pairs are `1 1`, `1 2`, `2 1`, `2 2`.
- Each `while` has exactly one `do` and one `end`.

## break inside while

`break` exits the innermost `while` loop immediately. The condition is not re-evaluated after `break`.

```lua
local n = 0
while n < 100 do
    n += 1
    if n == 10 then
        break
    end
end

print(n)    -- 10
```

**Breakdown**

- The loop would run until `n < 100` became false.
- At `n == 10`, `break` exits before the condition is checked again.
- `n` remains `10`.
- Any statements after `break` in the same block are unreachable.

## continue inside while

`continue` skips the rest of the current iteration and jumps to the condition check. Any statement placed after `continue` in the body does not run this iteration, so an update placed after `continue` will not advance the loop variable and the loop can hang.

```lua
local n = 0
while n < 10 do
    n += 1
    if n % 2 == 0 then
        continue
    end
    print(n)
end
```

**Breakdown**

- `n += 1` is placed before the `continue`, so the counter always advances.
- On even `n`, `continue` skips `print(n)` and returns to the condition.
- On odd `n`, `print(n)` runs.
- Placing `n += 1` after `continue` would cause the loop to never advance on even values.

## Locals inside the body

A `local` declared inside the body is recreated on each iteration. The binding goes out of scope at the end of that iteration and a fresh one is created for the next. The `while` condition cannot reference any such local; it must depend on values declared outside the loop or returned by the body through an assignment to an outer local.

```lua
local i = 0
while i < 3 do
    local doubled = i * 2
    print(doubled)
    i += 1
end
```

**Breakdown**

- `doubled` is a fresh local on each iteration.
- The condition `i < 3` reads `i`, which is declared outside the loop.
- `i += 1` updates the outer local, so the condition can eventually become false.
- `doubled` is not visible after `end`.

## while versus repeat

`while` checks the condition before the body; `repeat` checks it after. Choose `while` when the body should be skipped if the condition is false on entry, and when the condition does not depend on a value computed inside the body. Choose `repeat` when the body must run at least once, or when the condition needs a body-local value.

```lua
local n = 0

while n < 3 do
    n += 1
end

repeat
    n -= 1
until n == 0
```

**Breakdown**

- The `while` runs while `n < 3`, incrementing each iteration.
- The `repeat` runs the body first, decrementing, then checks `n == 0`.
- With `n == 0` on entry, `while` would skip, but `repeat` would still run once and set `n` to `-1`.

## Restrictions

`while` requires a condition and a `do` keyword. Omitting either is a syntax error. The body must be terminated by `end`; `until` is not valid for `while`, and `do` is not valid for `repeat`.

```lua
-- while do print("x") end            -- compile error: missing condition
-- while true print("x") end          -- compile error: missing do
-- while true do print("x")           -- compile error: missing end
-- while true do print("x") until x   -- compile error: while does not use until
```

**Breakdown**

- `while do` is rejected because the condition is missing.
- `while true print(...)` is rejected because `do` is missing.
- A `while` without `end` is rejected at the end of the enclosing block.
- `until` is valid only for `repeat`; it cannot close a `while` loop.

