# continue

The iteration skip statement. Ends the current iteration of the innermost enclosing loop and proceeds to the next iteration, without terminating the loop. `continue` is a Luau extension; it is not present in stock Lua. This page lists every loop it can skip within, every restriction the compiler enforces, and the interaction with loop counters that causes most bugs.

## Contents

- [Purpose](#purpose)
- [Inside a numeric for](#inside-a-numeric-for)
- [Inside a generic for](#inside-a-generic-for)
- [Inside a while loop](#inside-a-while-loop)
- [Inside a repeat loop](#inside-a-repeat-loop)
- [Inside nested loops](#inside-nested-loops)
- [Restriction: statements after continue](#restriction-statements-after-continue)
- [Restriction: outside a loop](#restriction-outside-a-loop)

## Purpose

`continue` exists to skip the rest of a loop iteration without ending the loop. It is the counterpart to `break`: where `break` leaves the loop entirely, `continue` leaves only the current pass.

```lua
for i = 1, 5 do
    if i % 2 == 0 then
        continue
    end
    print(i)
end
```

**Breakdown**

- The loop would print every value from `1` to `5`.
- On even `i`, `continue` skips the rest of that iteration, including `print(i)`.
- Only odd values `1`, `3`, `5` are printed.

## Inside a numeric for

In a numeric `for`, `continue` skips the body for the current index. The loop's own increment step runs normally, so the counter still advances.

```lua
local sum = 0
for i = 1, 10 do
    if i > 5 then
        continue
    end
    sum += i
end

print(sum)    -- 15
```

**Breakdown**

- `sum` accumulates `1 + 2 + 3 + 4 + 5`.
- When `i > 5`, `continue` skips the `sum += i` statement.
- The loop still runs to `10`, but nothing is added past `5`.
- The final sum is `15`.

## Inside a generic for

In a generic `for`, `continue` skips the body for the current pair and proceeds to the next pair. The iterator is called again normally.

```lua
local players = { "alice", "bob", "charlie" }

for index, name in ipairs(players) do
    if name == "bob" then
        continue
    end
    print(index, name)
end
```

**Breakdown**

- `ipairs` yields all three pairs.
- When `name == "bob"`, `continue` skips `print`.
- `1, "alice"` and `3, "charlie"` are printed.
- `2, "bob"` is not printed, but the iterator still advances to `3`.

## Inside a while loop

In a `while` loop, `continue` jumps back to the condition check. Any statement placed after `continue` in the body does not run this iteration, so an update placed after `continue` will not advance the counter and the loop can hang.

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

- `n += 1` runs before the `continue` check, so the counter always advances.
- On even `n`, `continue` skips `print(n)` and returns to the condition.
- On odd `n`, `print(n)` runs.
- If `n += 1` were placed after the `continue`, even values would skip the increment and the loop would never terminate.

## Inside a repeat loop

In a `repeat ... until` loop, `continue` jumps to the `until` condition check. The body restarts if the condition is still falsy.

```lua
local n = 0
repeat
    n += 1
    if n == 3 then
        continue
    end
    print(n)
until n >= 5
```

**Breakdown**

- `n += 1` runs first, then the `if` check.
- At `n == 3`, `continue` jumps to `until n >= 5`, which is false, so the loop restarts.
- `3` is not printed; `1`, `2`, `4`, `5` are printed.
- The condition is still evaluated on the iteration that ran `continue`.

## Inside nested loops

`continue` affects the innermost loop only. Outer loops are unaffected and continue their own iteration.

```lua
for row = 1, 3 do
    for col = 1, 3 do
        if col == 2 then
            continue
        end
        print(row, col)
    end
end
```

**Breakdown**

- The inner `continue` skips `col == 2` for each row.
- The outer loop still iterates through all three rows.
- Only `(row, 1)` and `(row, 3)` are printed for each row.
- There is no labelled `continue` in SLua; skipping in an outer loop requires a flag or a restructured function.

## Restriction: statements after continue

`continue` must be the last statement in its block. Any statement after `continue` in the same block is unreachable and rejected by the compiler.

```lua
for i = 1, 3 do
    continue
    print(i)    -- compile error
end
```

**Breakdown**

- `print(i)` follows `continue` in the same block.
- The compiler rejects this with a "statement is unreachable" error.
- Conditional skips must be wrapped in `if` so that `continue` sits at the end of the block.

## Restriction: outside a loop

`continue` outside any loop is a compile error, exactly like `break`. It has no meaning at the top level of a chunk, inside a function with no enclosing loop, or inside a `do ... end` block that is not itself inside a loop.

```lua
-- continue    -- compile error

local function f()
    -- continue    -- compile error
end
```

**Breakdown**

- A bare `continue` at the chunk level is rejected.
- A `continue` inside a function with no enclosing loop is rejected.
- `continue` becomes valid again as soon as it is inside a `for`, `while`, or `repeat` in the same function.

