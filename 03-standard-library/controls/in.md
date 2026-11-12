# in

The iteration clause keyword. Separates the loop variable list from the iterator expression inside a generic `for`. `in` appears exactly once per generic `for`, between the variable names and the expression whose results drive the iteration. It is not used in the numeric `for`, which uses `=` instead. This page lists every position where `in` is valid, the forms the expression after it can take, and the restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [With ipairs and pairs](#with-ipairs-and-pairs)
- [With a custom iterator function](#with-a-custom-iterator-function)
- [With the full iteration protocol](#with-the-full-iteration-protocol)
- [With a table directly](#with-a-table-directly)
- [With __iter](#with-__iter)
- [Multiple loop variables](#multiple-loop-variables)
- [Precedence with the expression after in](#precedence-with-the-expression-after-in)
- [Not used in numeric for](#not-used-in-numeric-for)
- [Restrictions](#restrictions)

## Purpose

`in` marks the boundary between the loop variables and the iterator in a generic `for`. The expression list after `in` produces the values the loop uses to drive iteration: the iterator function, an optional state, and an optional initial control value.

```lua
for k, v in pairs({ a = 1, b = 2 }) do
    print(k, v)
end
```

**Breakdown**

- `for k, v in ... do` declares two loop variables, `k` and `v`.
- `in` separates them from the expression that follows.
- `pairs({ a = 1, b = 2 })` is the iterator expression.
- The loop body runs once per key-value pair produced by `pairs`.

## With ipairs and pairs

The most common iterators on the right of `in` are `ipairs` and `pairs`. `ipairs` yields array index-value pairs; `pairs` yields every key-value pair. Both are called once before the loop begins and return the three values of the iteration protocol.

```lua
for i, v in ipairs({ "a", "b" }) do
    print(i, v)
end

for k, v in pairs({ x = 1, y = 2 }) do
    print(k, v)
end
```

**Breakdown**

- `ipairs({ "a", "b" })` yields `1, "a"` then `2, "b"`, stopping at the first `nil`.
- `pairs({ x = 1, y = 2 })` yields both pairs in an unspecified order.
- The variable list before `in` must match the iterator's arity; extra variables receive `nil`, missing ones are discarded.

## With a custom iterator function

The expression after `in` may be a user function that returns a single iterator. The `for` calls that iterator repeatedly with no arguments, stops when it returns `nil`, and assigns each non-nil return to the loop variable.

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
    print(value)       -- 1  2  3
end
```

**Breakdown**

- `range(3)` returns a function that acts as the iterator.
- The `for` calls the iterator with no arguments on each iteration.
- The iterator returns `1`, `2`, `3`, then `nil` to stop.
- Only one loop variable is used because the iterator returns one value.

## With the full iteration protocol

The expression list after `in` may supply up to three values: the iterator function, a state value passed to each call, and an initial control value. When three values are supplied, the iterator is called as `iterator(state, control)` and its return becomes the next control value.

```lua
local function iter(state: number, control: number): number?
    if control < state then
        return control + 1
    end
end

for i in iter, 3, 0 do
    print(i)           -- 1  2  3
end
```

**Breakdown**

- `iter` is the iterator function.
- `3` is the state passed to every call.
- `0` is the initial control value.
- On the first iteration, `iter(3, 0)` returns `1`, which becomes the next control value.
- The loop stops when `iter` returns `nil`.

## With a table directly

Luau allows a table to be written directly after `in`, without `ipairs` or `pairs`. The loop then follows the default table traversal, visiting the numeric keys up to the first `nil` in order, then the remaining keys in an unspecified order.

```lua
local data = { 10, 20, 30, name = "list" }

for k, v in data do
    print(k, v)
end
```

**Breakdown**

- `for k, v in data do` iterates the table directly.
- Numeric keys `1`, `2`, `3` are visited first, in order.
- The string key `name` follows, in an unspecified order.
- This is equivalent to `pairs(data)` but does not require the library call.

## With __iter

When a table or userdata defines an `__iter` metamethod, placing the object after `in` calls `__iter` once to obtain the three iteration values. This lets a class control how its instances are traversed without exposing the iterator explicitly.

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
    print(k, v)        -- 1 a   2 b
end
```

**Breakdown**

- `Node:__iter()` returns `next` as the iterator, `self.children` as the state, and `nil` as the control.
- Placing `tree` after `in` calls `__iter` on it, producing the three values.
- The loop then runs as if `next, self.children, nil` had been written after `in` directly.

## Multiple loop variables

The variable list before `in` may declare any number of names. The iterator's return values are assigned to them left to right; any extra returns are discarded, and any missing returns are `nil`.

```lua
for k, v, extra in ipairs({ "a", "b" }) do
    print(k, v, extra)   -- 1 a nil   2 b nil
end
```

**Breakdown**

- `ipairs` returns only two values per iteration.
- The third variable `extra` receives `nil` on every iteration.
- Declaring more variables than the iterator returns is allowed; the extras are simply `nil`.

## Precedence with the expression after in

Everything after `in` up to `do` is a single expression list. If the iterator is the result of a function call with arguments, the call must not be split by an operator; wrap complex expressions in parentheses when needed.

```lua
for v in makeIterator(10) do
    print(v)
end

for v in (chooseIterator()) do
    print(v)
end
```

**Breakdown**

- `makeIterator(10)` is called once before the loop; its result is the iterator.
- `(chooseIterator())` forces the entire call result to be treated as the iterator expression.
- Without the parentheses, chaining operators to a function call can change the parse; wrapping the expression removes the ambiguity.

## Not used in numeric for

The numeric `for` uses `=` between the loop variable and the start value, not `in`. Using `in` in a numeric loop, or `=` in a generic loop, is a syntax error.

```lua
-- for i in 1, 3 do ... end     -- compile error: numeric for uses =
-- for k = pairs(t) do ... end  -- compile error: generic for uses in
```

**Breakdown**

- `for i in 1, 3` is rejected; the numeric form expects `for i = 1, 3`.
- `for k = pairs(t)` is rejected; the generic form expects `for k in pairs(t)`.
- The two forms are distinguished by the token between the variable and the bounds or iterator.

## Restrictions

`in` requires a variable list on its left and at least one expression on its right. Omitting either side is a syntax error. The word `in` is reserved in SLua and cannot be used as an identifier.

```lua
-- for in pairs(t) do end        -- compile error: missing variables
-- for k in do end               -- compile error: missing expression
-- local in = 1                  -- compile error: reserved word
```

**Breakdown**

- `for in pairs(t)` is rejected because no loop variables are declared.
- `for k in do` is rejected because the expression list is empty.
- `in` is a reserved word; using it as a variable name is rejected at parse time.

