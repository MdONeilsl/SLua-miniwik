# for

The loop statement. SLua provides two forms: the **numeric for**, which iterates a variable over an arithmetic progression, and the **generic for**, which iterates over the values produced by an iterator. Both forms open a block with `do` and close it with `end`. The loop variable (or variables) are local to the loop body and cannot be used to alter the iteration. This page lists both forms, every way each can be written, the iteration protocol that the generic form follows, and the behaviour of `break` and `continue` inside each.

## Contents

- [Purpose](#purpose)
- [Numeric for](#numeric-for)
- [Numeric for: start, stop, step](#numeric-for-start-stop-step)
- [Numeric for: bounds are evaluated once](#numeric-for-bounds-are-evaluated-once)
- [Generic for: the iteration protocol](#generic-for-the-iteration-protocol)
- [Generic for: ipairs and pairs](#generic-for-ipairs-and-pairs)
- [Generalized iteration: iterating tables directly](#generalized-iteration-iterating-tables-directly)
- [Custom iterators: __iter](#custom-iterators-__iter)
- [Loop variables are local and read-only in effect](#loop-variables-are-local-and-read-only-in-effect)
- [Type annotations on loop variables](#type-annotations-on-loop-variables)
- [break inside a for](#break-inside-a-for)
- [continue inside a for](#continue-inside-a-for)
- [Nested for loops](#nested-for-loops)
- [Restrictions](#restrictions)

## Purpose

`for` exists to repeat a block a known number of times (numeric form) or once per value produced by an iterator (generic form). It is the only loop construct in SLua that declares its own loop variable.

```lua
for i = 1, 3 do
    print(i)
end

for index, value in ipairs({ "a", "b" }) do
    print(index, value)
end
```

**Breakdown**

- `for i = 1, 3 do ... end` is the numeric form; `i` takes the values `1`, `2`, `3`.
- `for index, value in ipairs(...) do ... end` is the generic form; the iterator produces `index, value` pairs.
- Both forms open a block with `do` and close it with `end`.

## Numeric for

The numeric form declares a single control variable and iterates it over an arithmetic progression. The syntax is `for name = start, stop [, step] do ... end`. The variable is assigned `start` on the first iteration and increased by `step` (default `1`) until it exceeds `stop`. When `step` is negative, the loop counts down.

```lua
for i = 1, 3 do
    print(i)          -- 1  2  3
end
```

**Breakdown**

- `for i = 1, 3 do` runs the body for `i = 1`, `i = 2`, `i = 3`.
- The loop stops when `i` would exceed `3`.
- `i` is local to the loop and is not visible after `end`.

## Numeric for: start, stop, step

A third value supplies the step. A positive step counts up; a negative step counts down. The loop stops when the control variable passes `stop` in the direction of the step, so `stop` is included only when the progression lands on it exactly.

```lua
for i = 10, 1, -2 do
    print(i)          -- 10  8  6  4  2
end

for i = 1, 10, 3 do
    print(i)          -- 1  4  7  10
end
```

**Breakdown**

- `for i = 10, 1, -2 do` counts down from `10` by `2`; values are `10`, `8`, `6`, `4`, `2`.
- `for i = 1, 10, 3 do` counts up from `1` by `3`; values are `1`, `4`, `7`, `10`.
- A step of `0` causes an error or an infinite loop depending on the engine; it is not a valid loop specification.
- The loop variable is never assigned a value beyond `stop`; the loop simply ends.

## Numeric for: bounds are evaluated once

The `start`, `stop`, and `step` expressions are evaluated once, before the first iteration. Changing any of them inside the body has no effect on the loop. The control variable itself is read-only in effect: assigning to it inside the body does not change the iteration.

```lua
local stop = 5
for i = 1, stop do
    stop = 1
    print(i)          -- 1  2  3  4  5
end
```

**Breakdown**

- `stop` is read once, before the loop begins.
- The body assigns `stop = 1`, but the loop continues to `5` because the bound was already captured.
- Assigning to `i` inside the body is allowed by the parser but has no effect on iteration; the next value of `i` is computed from the original progression.

## Generic for: the iteration protocol

The generic form declares a list of loop variables and evaluates an expression list after `in`. The first result of that expression must be an iterator function; the remaining results, if any, are passed as state and control values. On each iteration the iterator function is called with `(state, control)`, and its first return value becomes the new control value. The loop stops when the control value is `nil`.

```lua
local function range(n: number)
    local i = 0
    return function()
        i += 1
        if i <= n then
            return i
        end
    end
end

for value in range(3) do
    print(value)      -- 1  2  3
end
```

**Breakdown**

- `range(3)` returns a function that acts as the iterator.
- The `for` calls the iterator repeatedly with no state or control values because none were supplied.
- Each call returns the next number or `nil` to stop.
- The loop body runs for each non-`nil` return.

## Generic for: ipairs and pairs

Two library iterators cover most table traversal. `ipairs` walks the array part of a table in index order, starting at `1` and stopping at the first `nil`. `pairs` walks every key-value pair, including non-numeric keys, in an unspecified order.

```lua
local arr = { "a", "b", "c" }
for i, v in ipairs(arr) do
    print(i, v)       -- 1 a   2 b   3 c
end

local rec = { x = 1, y = 2 }
for k, v in pairs(rec) do
    print(k, v)       -- x 1   y 2   (order may vary)
end
```

**Breakdown**

- `ipairs(arr)` yields `1, "a"`, `2, "b"`, `3, "c"`; it stops at the first `nil` index.
- `pairs(rec)` yields every key-value pair in an order that may differ between runs.
- Use `ipairs` for arrays; use `pairs` for dictionaries and for tables whose keys may be non-numeric.

## Generalized iteration: iterating tables directly

Luau, and therefore SLua, extends the generic form so that a table may be written directly after `in` without `ipairs` or `pairs`. The loop then follows a default traversal: first the numeric keys `1..k` up to the first `nil`, then the remaining keys in unspecified order.

```lua
local data = { 10, 20, 30, name = "list" }

for k, v in data do
    print(k, v)
end
```

**Breakdown**

- `for k, v in data do` iterates the table without a library iterator.
- Numeric keys `1`, `2`, `3` are visited first, in order.
- The string key `name` is visited afterward, in an unspecified order.
- This form is equivalent to `pairs(data)` in effect, but it works directly on the table value.

## Custom iterators: __iter

A table or userdata may define an `__iter` metamethod to control what the generic `for` yields when the object itself is placed after `in`. The metamethod is called once, before the loop begins, and must return the three values of the iteration protocol: a generator function, a state, and an initial control value. If `__iter` is absent, the default table traversal applies.

```lua
local Node = {}
Node.__index = Node

function Node.new(children)
    return setmetatable({ children = children }, Node)
end

function Node:__iter()
    return next, self.children, nil
end

local tree = Node.new({ "a", "b" })
for k, v in tree do
    print(k, v)       -- 1 a   2 b
end
```

**Breakdown**

- `Node:__iter()` returns `next` as the generator, `self.children` as the state, and `nil` as the initial control value.
- The `for` calls `next(self.children, nil)` on the first iteration, then `next(self.children, previous_key)` on subsequent ones.
- The loop stops when `next` returns `nil`.
- If `Node` did not define `__iter`, the loop would iterate the fields of the `Node` object itself, not its children.

## Loop variables are local and read-only in effect

The variables declared by the `for` header are local to the loop body. In the numeric form, the control variable is managed by the loop and assigning to it inside the body does not change the iteration. In the generic form, the visible variables are fresh bindings on each iteration; assigning to them affects only the current copy and not the iterator state.

```lua
for i = 1, 3 do
    i = 10
    print(i)          -- 10  10  10
end

for k, v in ipairs({ "a", "b" }) do
    v = "changed"
    print(k, v)       -- 1 changed   2 changed
end
```

**Breakdown**

- `i = 10` inside the numeric body changes the visible `i` but not the loop's internal progression; the next iteration still begins from the original sequence.
- `v = "changed"` inside the generic body replaces the local copy of the value; the iterator still produces the original table values on the next iteration.
- The loop variables are not visible after `end`.

## Type annotations on loop variables

Under strict mode, each loop variable may carry a type annotation. The annotation follows the variable name and a colon, the same syntax used for locals and parameters.

```lua
for i: number = 1, 3 do
    print(i)
end

for k: string, v: number in pairs({ a = 1 }) do
    print(k, v)
end
```

**Breakdown**

- `for i: number = 1, 3 do` declares `i` as `number`.
- `for k: string, v: number in pairs(...) do` declares both loop variables with their types.
- The annotations are checked by the type checker; a mismatch in the iterator's return types is reported.

## break inside a for

`break` exits the innermost `for` loop immediately. The iterator is not called again, and any remaining values are never produced.

```lua
for i = 1, 10 do
    if i == 4 then
        break
    end
    print(i)          -- 1  2  3
end
```

**Breakdown**

- `break` runs when `i == 4`.
- The loop stops before `print(i)` can print `4`.
- The remaining values `5` through `10` are never produced.

## continue inside a for

`continue` skips the rest of the current iteration and proceeds to the next. In a numeric `for`, the increment runs normally. In a generic `for`, the iterator is called again normally.

```lua
for i = 1, 5 do
    if i % 2 == 0 then
        continue
    end
    print(i)          -- 1  3  5
end
```

**Breakdown**

- On even `i`, `continue` skips `print(i)`.
- The loop still runs for every value from `1` to `5`.
- Only odd values are printed.

## Nested for loops

`for` loops nest to any depth. `break` and `continue` apply to the innermost enclosing loop only. There is no labelled `break` or `continue`; to leave or skip across multiple levels, use a flag or restructure into a function that returns early.

```lua
for row = 1, 2 do
    for col = 1, 2 do
        if col == 2 then
            break
        end
        print(row, col)   -- 1 1   2 1
    end
end
```

**Breakdown**

- The inner `break` fires when `col == 2`.
- Only the inner loop exits; the outer loop continues to the next row.
- The output is `1 1` and `2 1`; `1 2` and `2 2` are never printed.

## Restrictions

The numeric form requires `=` between the variable and the start value, and at least two values after it (start and stop). The generic form requires `in` between the variable list and the expression list. Omitting either is a syntax error.

```lua
-- for i 1, 3 do end          -- compile error: missing =
-- for v ipairs({}) do end     -- compile error: missing in
```

**Breakdown**

- `for i 1, 3 do` is rejected because the `=` is missing.
- `for v ipairs({}) do` is rejected because the `in` is missing.
- The `do` keyword is mandatory in both forms; omitting it is also a syntax error.
