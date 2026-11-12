# return

The function exit statement. Ends the current function or chunk immediately and passes zero or more values back to the caller. `return` may appear anywhere a statement is allowed, but only as the last statement of its block. Inside a function, it returns to the caller. At the top level of a script or module, it ends the chunk and its values become the result of the chunk. This page lists every position where `return` is valid, every form it can take, and the two restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [Returning no values](#returning-no-values)
- [Returning one value](#returning-one-value)
- [Returning multiple values](#returning-multiple-values)
- [Returning a call expression](#returning-a-call-expression)
- [Return from a function](#return-from-a-function)
- [Return from a chunk](#return-from-a-chunk)
- [Return inside conditionals and loops](#return-inside-conditionals-and-loops)
- [return as the last statement](#return-as-the-last-statement)
- [Restriction: statements after return](#restriction-statements-after-return)
- [Restriction: only inside a function or chunk](#restriction-only-inside-a-function-or-chunk)

## Purpose

`return` ends the current function or chunk. Every `return` takes effect immediately: any statement after it in the same block is unreachable, and any enclosing loop or block is abandoned. It is the only statement that produces a value from a function.

```lua
local function square(n: number): number
    return n * n
end

print(square(4))    -- 16
```

**Breakdown**

- `return n * n` ends `square` and returns the product.
- The caller receives the value as the result of the call.
- The function body has no further statements to run.

## Returning no values

A bare `return` ends the function with no result. The caller receives zero values. This is the standard way to exit early when the function's return type is empty or when there is nothing to return.

```lua
local function log(msg: string): ()
    if msg == "" then
        return
    end
    print(msg)
end
```

**Breakdown**

- `return` with no expression ends the function immediately.
- The function's annotation `(): ()` declares that it returns no values.
- The early `return` skips the `print(msg)` when `msg` is empty.
- A function with no `return` at all behaves the same as one ending with a bare `return`.

## Returning one value

`return expr` evaluates `expr` and returns its value to the caller. The expression is evaluated before the function exits, so any side effects in it run first.

```lua
local function double(n: number): number
    return n * 2
end

local x = double(21)    -- 42
```

**Breakdown**

- `return n * 2` evaluates `n * 2` and returns the result.
- `local x = double(21)` binds `x` to the returned value, `42`.
- The value's type must match the return annotation; here, `number`.

## Returning multiple values

`return a, b, c` returns any number of values. Callers capture them into matching variables, discard extras, or pack them into a table. When the call appears in a non-tail position of an expression list, only the first returned value is used.

```lua
local function minmax(a: number, b: number): (number, number)
    if a < b then
        return a, b
    end
    return b, a
end

local lo, hi = minmax(3, 7)    -- 3, 7
local first = minmax(3, 7)     -- 3
```

**Breakdown**

- `return a, b` returns two values.
- `local lo, hi = ...` captures both.
- `local first = ...` captures only the first; the second is discarded.
- The return annotation `(number, number)` declares both values.

## Returning a call expression

When `return` is followed by a call, the call's own returns become the function's returns. This is a tail return: the function passes through the call's results without inspecting them.

```lua
local function forward(...: any): ...any
    return process(...)
end
```

**Breakdown**

- `return process(...)` calls `process` and returns whatever it returns.
- Any number of values from `process` reach the caller of `forward`.
- The annotation `...any` accepts and returns any number of values.
- Tail returns are the idiomatic way to forward varargs or delegate to a helper.

## Return from a function

Inside a function, `return` ends the function's execution and yields control to the caller. Any block the function opened is unwound: `do` blocks, `if` chains, and loops all end. Locals declared inside the function go out of scope.

```lua
local function find(items: {number}, target: number): number?
    for i = 1, #items do
        if items[i] == target then
            return i
        end
    end
    return nil
end
```

**Breakdown**

- The first `return i` exits both the `if` and the `for` loop.
- `return nil` at the end handles the case where the target was not found.
- The annotation `number?` marks the result as optional.
- The function has one entry point and multiple exit points, all through `return`.

## Return from a chunk

At the top level of a script or module, `return` ends the chunk and produces the chunk's result. In a module, the value returned is what the importer receives from `require`. In a script, the returned value is not observed by the engine, but `return` still ends the chunk.

```lua
local module = {}

function module.hello(): ()
    print("hello")
end

return module
```

**Breakdown**

- `return module` ends the chunk and yields the module table.
- Importers of this module receive the table as the result of `require`.
- A top-level `return` must be the last statement of the chunk.
- Mixing `export` declarations with a top-level `return` is a compile error; use one style or the other.

## Return inside conditionals and loops

`return` may appear inside any block. When it executes, it ends the function immediately, abandoning the enclosing conditional or loop. The rest of the block is unreachable.

```lua
local function classify(n: number): string
    if n < 0 then
        return "negative"
    end
    for i = 1, 3 do
        if i == n then
            return "small positive"
        end
    end
    return "other"
end
```

**Breakdown**

- Each `return` exits the function; the `if` and `for` are abandoned.
- With `n == 2`, the inner `return "small positive"` executes and the loop stops.
- With `n == 0`, neither branch returns and the function falls through to `return "other"`.
- The annotation `string` matches every return value.

## return as the last statement

`return` must be the last statement in its block. It may be followed by `end` (closing the block) or by `until` (closing a `repeat`), but not by any further statement in the same block. This rule exists because the parser cannot tell when a `return` is followed by a statement whether that statement is part of the same block or of the enclosing construct.

```lua
local function ok(): number
    return 1
end

local function alsoOk(): number
    return 1
--  print("unreachable")    -- compile error
end
```

**Breakdown**

- `return 1` followed immediately by `end` is valid.
- `return 1` followed by `print(...)` in the same block is rejected.
- The compiler reports a "statement is unreachable" error before running.
- Place cleanup before `return`, not after.

## Restriction: statements after return

Any statement after `return` in the same block is unreachable and rejected by the compiler. This applies whether the statement is another `return`, an assignment, a call, or a nested block.

```lua
local function bad(): number
    return 1
--  return 2                -- compile error: unreachable
end
```

**Breakdown**

- The second `return 2` follows the first in the same block.
- The compiler rejects it before compilation.
- To choose between values, use a conditional: `if cond then return 1 else return 2 end`.

## Restriction: only inside a function or chunk

`return` is valid only inside a function or at the top level of a chunk. It is not valid inside a plain `do ... end` block that is not itself inside a function or chunk, nor inside a `for` or `while` that is not inside a function or chunk.

```lua
-- do
--     return 1            -- compile error: not inside a function
-- end

-- for i = 1, 3 do
--     return i            -- compile error
-- end
```

**Breakdown**

- `return` inside a bare `do` block at the chunk level is rejected; it has no enclosing function to return from.
- `return` inside a loop at the chunk level is rejected for the same reason.
- Both become valid once the block or loop is placed inside a function.
