# break

The loop exit statement. Terminates the innermost enclosing loop immediately and transfers control to the first statement after the loop's `end`. `break` is only valid inside a loop; anywhere else it is a compile error. This page lists every loop it can exit, every way it can appear, and the restrictions the compiler enforces.

## Contents

- [Purpose](#purpose)
- [Inside a numeric for](#inside-a-numeric-for)
- [Inside a generic for](#inside-a-generic-for)
- [Inside a while loop](#inside-a-while-loop)
- [Inside a repeat loop](#inside-a-repeat-loop)
- [Inside nested loops](#inside-nested-loops)
- [Restriction: statements after break](#restriction-statements-after-break)
- [Restriction: outside a loop](#restriction-outside-a-loop)

## Purpose

`break` exists to end a loop before its natural termination condition is reached. It is the only way to leave a `for`, `while`, or `repeat` loop from the middle of its body.

```lua
for i = 1, 10 do
    if i == 5 then
        break
    end
    print(i)
end
```

**Breakdown**

- The loop would run from `1` to `10`.
- When `i == 5`, the condition is true and `break` runs.
- `print(i)` executes for `1`, `2`, `3`, `4` only.
- Control resumes at the first statement after `end`.

## Inside a numeric for

A numeric `for` stops counting as soon as `break` executes. The loop variable goes out of scope and the next increment never happens.

```lua
local target = 7
local found: number? = nil

for i = 1, 100 do
    if i * i > target then
        found = i
        break
    end
end

print(found)    -- 3
```

**Breakdown**

- The loop scans from `1` upward until `i * i` exceeds `target`.
- At `i = 3`, `i * i == 9`, which is greater than `7`, so `found` is set and `break` runs.
- The loop stops; no further `i` is evaluated.
- `print(found)` prints `3`.

## Inside a generic for

A generic `for` stops iterating as soon as `break` executes. The iterator is not called again, so any remaining keys, values, or results are never produced.

```lua
local players = { "alice", "bob", "charlie" }

for index, name in ipairs(players) do
    if name == "bob" then
        break
    end
    print(index, name)
end
```

**Breakdown**

- `ipairs` yields `1, "alice"`, then `2, "bob"`, then `3, "charlie"` on demand.
- On the second iteration, `name == "bob"` is true, so `break` runs before `print`.
- `ipairs` is never called a third time; `"charlie"` is not visited.
- Only `1, "alice"` is printed.

## Inside a while loop

A `while` loop stops as soon as `break` executes. The condition is not re-evaluated for the iteration that would have followed.

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
- `n` increments on each iteration.
- At `n == 10`, `break` runs and the loop exits before the condition is checked again.
- `n` remains `10`.

## Inside a repeat loop

A `repeat ... until` loop stops as soon as `break` executes. The `until` condition is not evaluated for the iteration that would have followed.

```lua
local n = 0
repeat
    n += 1
    if n == 5 then
        break
    end
until n >= 10

print(n)    -- 5
```

**Breakdown**

- The loop would run until `n >= 10` became true.
- `n` increments on each iteration.
- At `n == 5`, `break` runs before `until n >= 10` is evaluated.
- `n` remains `5`.

## Inside nested loops

`break` exits the innermost enclosing loop only. The outer loop continues normally. There is no labelled `break` in SLua; to leave multiple levels at once, use a flag or move the search into a function that returns early.

```lua
local grid = { {1, 2, 3}, {4, 5, 6} }

for row = 1, #grid do
    for col = 1, #grid[row] do
        if grid[row][col] == 4 then
            break
        end
        print(row, col, grid[row][col])
    end
    print("row done", row)
end
```

**Breakdown**

- The inner `break` fires when the cell equals `4`, which happens at row `2`, column `1`.
- Only the inner loop exits; the outer loop proceeds to its next iteration.
- `print("row done", row)` still runs for both rows.
- The outer loop has no `break`, so it completes.

## Restriction: statements after break

Any statement after `break` in the same block is unreachable and rejected by the compiler. Write `break` as the last statement of its block.

```lua
for i = 1, 5 do
    if i == 3 then
        break
        print("never")    -- compile error
    end
end
```

**Breakdown**

- `print("never")` follows `break` in the same block.
- The compiler rejects this with a "statement is unreachable" error.
- Any cleanup that must run before exiting belongs before `break`, not after.

## Restriction: outside a loop

`break` outside any loop is a compile error. It has no meaning at the top level of a chunk, inside a plain function with no enclosing loop, or inside a `do ... end` block that is not itself inside a loop.

```lua
-- break        -- compile error

local function f()
    -- break    -- compile error
end
```

**Breakdown**

- A bare `break` at the chunk level is rejected.
- A `break` inside a function with no enclosing loop is rejected.
- `break` becomes valid again as soon as it is inside a `for`, `while`, or `repeat` in the same function.

