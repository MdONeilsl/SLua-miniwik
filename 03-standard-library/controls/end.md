# end

The block terminator. Closes an `if` statement, a `while` loop, a `for` loop, a `function` declaration, or a standalone `do` block. Every block that opens with one of those keywords must eventually close with `end`. The `repeat ... until` loop is the one exception: it closes with `until`, not `end`. This page lists every construct that requires `end`, what the closing marks in each, and the two places where `end` must not appear.

## Contents

- [Purpose](#purpose)
- [Closing an if statement](#closing-an-if-statement)
- [Closing a while loop](#closing-a-while-loop)
- [Closing a numeric for loop](#closing-a-numeric-for-loop)
- [Closing a generic for loop](#closing-a-generic-for-loop)
- [Closing a function declaration](#closing-a-function-declaration)
- [Closing a do block](#closing-a-do-block)
- [Nesting and matching](#nesting-and-matching)
- [Not used in repeat ... until](#not-used-in-repeat--until)
- [Not used in elseif or else](#not-used-in-elseif-or-else)

## Purpose

`end` marks the boundary of a block. At the matching `end`, any locals declared inside the block go out of scope, and control returns to the construct that opened it. Every construct that introduces a block must have a corresponding `end`, and the parser rejects any file where they do not match.

```lua
if true then
    print("inside")
end
```

**Breakdown**

- `if true then` opens the block.
- `print("inside")` is inside the block.
- `end` closes the block.
- Without `end`, the file does not parse.

## Closing an if statement

An `if` chain, with or without `elseif` and `else`, closes with a single `end`. The `end` belongs to the whole chain, not to any individual `elseif`.

```lua
local score = 75

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
else
    print("F")
end
```

**Breakdown**

- `if score >= 90 then` opens the chain.
- Each `elseif` adds a branch but does not open or close its own block.
- `else` adds the default branch.
- A single `end` closes the entire chain.
- Adding an extra `end` after the `elseif` is a syntax error.

## Closing a while loop

A `while` loop closes with `end`. The `end` closes both the loop body and the `while` statement.

```lua
local n = 0
while n < 3 do
    print(n)
    n += 1
end
```

**Breakdown**

- `while n < 3 do` opens the loop.
- `print(n)` and `n += 1` are inside the body.
- `end` closes the loop.
- The body runs while the condition remains truthy; `end` is reached each time the body finishes, and the condition is re-tested.

## Closing a numeric for loop

A numeric `for` loop closes with `end`. The `end` closes both the loop body and the `for` statement.

```lua
for i = 1, 3 do
    print(i)
end
```

**Breakdown**

- `for i = 1, 3 do` opens the loop.
- `print(i)` is inside the body.
- `end` closes the loop.
- The body runs once per index value; `end` is reached each time the body finishes, and the next index is computed.

## Closing a generic for loop

A generic `for` loop closes with `end`. The `end` closes both the loop body and the `for` statement.

```lua
for key, value in pairs({ a = 1, b = 2 }) do
    print(key, value)
end
```

**Breakdown**

- `for key, value in pairs(...) do` opens the loop.
- `print(key, value)` is inside the body.
- `end` closes the loop.
- The body runs once per key-value pair produced by the iterator.

## Closing a function declaration

A function declaration closes with `end`. This applies to `local function`, `function name(...)`, and anonymous `function(...)` expressions.

```lua
local function greet(name: string): string
    return "hello, " .. name
end
```

**Breakdown**

- `local function greet(...)` opens the function body.
- `return ...` is inside the body.
- `end` closes the function.
- The `end` is required whether the function is named or anonymous; an anonymous function expression still needs its own `end`.

## Closing a do block

A standalone `do ... end` block closes with `end`. The `end` closes the block and ends the scope of its locals.

```lua
do
    local x = 1
    print(x)
end
```

**Breakdown**

- `do` opens the block.
- `local x = 1` is inside the block.
- `print(x)` is inside the block.
- `end` closes the block; `x` goes out of scope.

## Nesting and matching

Blocks nest. Each `end` matches the most recent unclosed block. With nested `if`, `for`, and `function` constructs, the indentation guides the eye but does not affect matching; only the sequence of openers and `end`s matters.

```lua
local function process(items: {number})
    for i = 1, #items do
        if items[i] > 0 then
            print(items[i])
        end
    end
end
```

**Breakdown**

- The first `end` closes the inner `if`.
- The second `end` closes the `for` loop.
- The third `end` closes the function.
- Mismatched nesting produces a parse error; the compiler reports the line of the unclosed opener.

## Not used in repeat ... until

A `repeat ... until` loop does not use `end`. `repeat` opens the body directly; `until cond` closes the body and the loop. Adding an `end` after `until` is a syntax error.

```lua
local n = 0
repeat
    n += 1
until n == 3
```

**Breakdown**

- `repeat` opens the body.
- `until n == 3` closes the body and the loop.
- Writing `repeat ... until cond end` is rejected; the parser does not expect `end` after `until`.

## Not used in elseif or else

An `elseif` or `else` branch does not close with its own `end`. They are part of the enclosing `if` chain, and the chain closes with a single `end` after the final branch.

```lua
if a then
    print("a")
elseif b then
    print("b")
else
    print("c")
end
```

**Breakdown**

- `if a then` opens the chain.
- `elseif b then` adds a branch; no `end` here.
- `else` adds the default branch; no `end` here.
- A single `end` after the last branch closes the whole chain.
- Writing an `end` after `elseif` or `else` is a syntax error.
