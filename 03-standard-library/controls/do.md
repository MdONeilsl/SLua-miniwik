# do

The block introducer. `do` marks the beginning of a block whose locals go out of scope at the matching `end`. It appears in two roles: as the opening of a standalone `do ... end` block that groups statements into a new lexical scope, and as the keyword that opens the body of a `while` or `for` loop. It does not appear in `repeat ... until`; that loop opens its body directly. This page lists every position where `do` is valid, every position where it is required, and the one loop where it is a compile error.

## Contents

- [Purpose](#purpose)
- [Standalone do block](#standalone-do-block)
- [Standalone do block for temporary lifetimes](#standalone-do-block-for-temporary-lifetimes)
- [While loop body](#while-loop-body)
- [Numeric for body](#numeric-for-body)
- [Generic for body](#generic-for-body)
- [Repeat loop: do is not used](#repeat-loop-do-is-not-used)
- [Nesting](#nesting)

## Purpose

`do` opens a lexical block. Used standalone, it limits the lifetime of locals declared inside. Used in a loop, it introduces the body that repeats. Either way, the closing `end` marks the point where the block's locals go out of scope.

```lua
do
    local x = 1
    print(x)
end

-- print(x)    -- compile error
```

**Breakdown**

- `do ... end` creates a new block.
- `local x = 1` is scoped to that block.
- After `end`, `x` no longer exists and any reference to it is a compile error.

## Standalone do block

A `do ... end` block that is not part of a loop groups statements and confines the locals declared inside. It runs once, in order, then exits. Locals declared inside shadow same-named locals outside.

```lua
local x = 1
do
    local x = 2
    print(x)    -- 2
end
print(x)        -- 1
```

**Breakdown**

- The outer `x` is `1`.
- Inside the block, `local x = 2` shadows the outer `x`.
- Inside the block, `print(x)` prints `2`.
- After `end`, the outer `x` is visible again and prints `1`.
- Without the inner `local`, the block would assign to the outer `x`.

## Standalone do block for temporary lifetimes

A standalone `do ... end` block is the standard way to limit the lifetime of a large temporary so it becomes eligible for garbage collection sooner, while leaving the result available outside the block.

```lua
local result
do
    local buffer = {}
    for i = 1, 10000 do
        buffer[i] = i
    end
    result = #buffer
end
print(result)   -- 10000
```

**Breakdown**

- `buffer` is a large table built inside the block.
- After `end`, `buffer` goes out of scope and can be collected.
- `result` was declared outside the block, so its value survives and is printed as `10000`.

## While loop body

In a `while` loop, `do` marks the start of the body that repeats on each iteration. The `while` condition is evaluated before each pass.

```lua
local n = 0
while n < 3 do
    print(n)
    n += 1
end
```

**Breakdown**

- `do` opens the body of the loop.
- `end` closes both the body and the `while` statement.
- The body runs while `n < 3`, printing `0`, `1`, `2`.
- `do` is mandatory here; omitting it is a syntax error.

## Numeric for body

In a numeric `for` loop, `do` marks the start of the body that runs once per index value.

```lua
for i = 1, 3 do
    print(i)
end
```

**Breakdown**

- `do` opens the body of the loop.
- The body runs for `i = 1`, `2`, `3`.
- `end` closes the loop.
- `do` is mandatory here; omitting it is a syntax error.

## Generic for body

In a generic `for` loop, `do` marks the start of the body that runs once per iterator result.

```lua
for key, value in pairs({ a = 1, b = 2 }) do
    print(key, value)
end
```

**Breakdown**

- `do` opens the body of the loop.
- The body runs once per key-value pair produced by `pairs`.
- `end` closes the loop.
- `do` is mandatory here; omitting it is a syntax error.

## Repeat loop: do is not used

A `repeat ... until` loop does **not** use `do`. `repeat` opens the body directly, and `until cond` closes the body and the loop. Adding a `do` after `repeat` is a compile error. This is a common pitfall when converting a `while` loop to a `repeat` loop.

```lua
local n = 0
repeat
    n += 1
until n == 3
```

**Breakdown**

- `repeat` opens the body directly; there is no `do`.
- `until n == 3` closes the body and the loop.
- Writing `repeat do ... until cond` is a compile error; the parser expects a statement immediately after `repeat`.

## Nesting

`do` blocks nest to any depth. Each block opens a new scope; a local declared inside one block is not visible in any sibling or parent block.

```lua
do
    local a = 1
    do
        local b = 2
        print(a, b)     -- 1  2
    end
    -- print(b)         -- compile error
end
```

**Breakdown**

- The outer block declares `a`.
- The inner block declares `b` and can read both `a` and `b`.
- After the inner `end`, `b` is out of scope; referencing it is a compile error.
- After the outer `end`, `a` is out of scope as well.

