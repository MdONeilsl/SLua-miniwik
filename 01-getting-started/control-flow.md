[README](README.md) · [syntax](syntax.md) · [types](types.md) · [functions](functions.md) · [scripts](scripts.md)

# Control flow

The statements that decide which lines run. Conditionals select a branch; loops repeat a block; `break`, `continue`, and `return` move execution out of them. Every construct here is a statement, not an expression; nothing here produces a value.

## Contents

- [if / elseif / else](#if--elseif--else)
- [Truthiness](#truthiness)
- [while](#while)
- [repeat / until](#repeat--until)
- [Numeric for](#numeric-for)
- [Generic for](#generic-for)
- [break](#break)
- [continue](#continue)
- [return](#return)
- [do blocks](#do-blocks)
- [Nested loops](#nested-loops)


## if / elseif / else
---
Selects one branch out of several. The condition is any expression; `nil` and `false` are falsy, everything else is truthy. Branches are tested top to bottom and the first truthy condition wins. `else` catches the remainder.

```lua
local score = 75

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

- `if cond then ... end` runs the body only when `cond` is truthy.
- `elseif cond then ... end` runs only if every previous condition was falsy and `cond` is truthy.
- `else ... end` runs when every previous condition was falsy.
- `end` closes the whole statement; each `elseif` does not need its own `end`.
- There is no `switch`; a chain of `elseif` is the idiomatic form.

## Truthiness
---
There are exactly two falsy values: `nil` and `false`. Everything else, including `0`, `""`, and empty tables, is truthy. This differs from many other languages and is a frequent source of bugs when porting code.

```lua
if 0 then print("runs") end
if "" then print("runs") end
if nil then print("never") end
if false then print("never") end
```

**Breakdown**

- `0` is truthy.
- `""` (empty string) is truthy.
- `nil` is falsy.
- `false` is falsy.
- Test emptiness explicitly with `#s == 0`, `next(t) == nil`, or `value ~= 0`; do not rely on truthiness.

## while
---
Repeats a block while its condition stays truthy. The condition is evaluated before each iteration; if it is falsy on entry, the body never runs.

```lua
local count = 0
while count < 5 do
    count += 1
end
```

**Breakdown**

- `while cond do ... end` runs the body while `cond` is truthy.
- The condition is re-evaluated at the start of every iteration, including the first.
- `+=` is compound assignment; `count += 1` is equivalent to `count = count + 1`.

## repeat / until
---
Repeats a block until a condition becomes truthy. The condition is evaluated after the body, so the body always runs at least once. Locals declared inside the body are in scope inside the `until` expression.

```lua
local n = 10
repeat
    n -= 1
until n == 0
```

**Breakdown**

- `repeat ... until cond` runs the body first, then checks `cond`.
- The body runs at least once regardless of `cond`.
- Locals declared inside the body are visible to `cond`; this is the main reason to choose `repeat` over `while`.

## Numeric for
---
Iterates a variable over an arithmetic progression: a start value, a stop value, and an optional step.

```lua
for i = 1, 5 do
    print(i)
end

for i = 10, 1, -2 do
    print(i)
end
```

**Breakdown**

- `for i = start, stop do ... end` sets `i` to `start` and increments by 1 until `i` exceeds `stop` (inclusive).
- `for i = start, stop, step do ... end` increments by `step`; a negative `step` counts down.
- The loop variable is local to the loop and cannot be reassigned inside the body.
- The bounds are evaluated once at loop entry; changing them inside the body has no effect on iteration.

## Generic for
---
Iterates values produced by an iterator. `ipairs` walks array-shaped tables in index order; `pairs` walks every key in an unspecified order; a `__iter` metamethod or a custom iterator function also works.

```lua
local arr = { "a", "b", "c" }
for i, v in ipairs(arr) do
    print(i, v)
end

local rec = { x = 1, y = 2 }
for k, v in pairs(rec) do
    print(k, v)
end
```

**Breakdown**

- `for k, v in iter do ... end` calls `iter` repeatedly; each call returns a key-value pair, or `nil` to stop.
- `ipairs(t)` returns `1, t[1]`, `2, t[2]`, and so on, stopping at the first `nil` index.
- `pairs(t)` returns every key-value pair, in an order that may differ between iterations and between runs.
- Use `ipairs` for arrays, `pairs` for dictionaries, and `next` directly only when you need to inspect one pair at a time.

## break
---
Exits the innermost loop immediately. Control resumes at the statement after the loop's `end`. `break` is only valid inside a loop.

```lua
for i = 1, 10 do
    if i == 5 then
        break
    end
    print(i)
end
```

**Breakdown**

- `break` stops the closest enclosing loop, whether `for`, `while`, or `repeat`.
- Statements after `break` in the same block are unreachable.
- `break` inside a nested loop affects only the inner loop; there is no labelled `break`.

## continue
---
Skips the remainder of the current iteration and moves to the next. Luau extension; not present in stock Lua.

```lua
for i = 1, 5 do
    if i % 2 == 0 then
        continue
    end
    print(i)
end
```

**Breakdown**

- `continue` ends the current iteration of the innermost loop.
- The loop's own step (increment or next iterator call) proceeds normally.
- `continue` outside a loop is a compile error.
- `continue` must be the last statement in its block; a trailing expression after it is unreachable.

## return
---
Ends the current function and passes values back to the caller. A bare `return` ends the function with no results.

```lua
local function max(a: number, b: number): number
    if a > b then
        return a
    end
    return b
end
```

**Breakdown**

- `return expr` ends the function and returns `expr`.
- `return a, b` returns multiple values.
- `return` with no expression ends the function with no result.
- Code after `return` in the same block is unreachable and rejected by the compiler.
- `return` is valid only inside a function; at the top level of a script, `return` ends the chunk.

## do blocks
---
`do ... end` groups statements into a new scope without introducing a loop or a function. Variables declared inside are not visible outside.

```lua
local x = 1
do
    local x = 2
    print(x)      -- 2
end
print(x)          -- 1
```

**Breakdown**

- `do ... end` creates a new scope.
- A `local` inside the block shadows any same-named variable outside.
- The block runs once; its locals go out of scope at `end`.
- Common uses: limiting the lifetime of a large temporary, avoiding name clashes in a long chunk, and grouping initialisation that should not leak bindings.

## Nested loops
---
Loops may be nested to any depth. Each `break` and `continue` applies to the innermost enclosing loop only; to leave multiple levels, use a flag or restructure into a function that returns early.

```lua
local grid = { {1, 2}, {3, 4} }

for row = 1, #grid do
    for col = 1, #grid[row] do
        print(row, col, grid[row][col])
    end
end
```

**Breakdown**

- The outer `for` walks rows; the inner `for` walks columns within the current row.
- `#grid` is the number of rows; `#grid[row]` is the number of cells in that row.
- A `break` inside the inner loop exits only the inner loop; the outer loop continues to the next row.
