[README](README.md) · [syntax](syntax.md) · [types](types.md) · [control-flow](control-flow.md) · [scripts](scripts.md)

# Functions

How to declare, call, and pass functions in SLua. Functions are first-class values: they can be stored, passed as arguments, and returned from other functions. Annotation syntax for parameters and returns is covered in [syntax](syntax.md); the type itself is listed in [types](types.md).

## Contents

- [Declaring a function](#declaring-a-function)
- [Anonymous functions](#anonymous-functions)
- [Methods and the colon](#methods-and-the-colon)
- [Parameters and annotations](#parameters-and-annotations)
- [Multiple returns](#multiple-returns)
- [Varargs](#varargs)
- [Closures](#closures)
- [Higher-order functions](#higher-order-functions)
- [Recursion](#recursion)
- [Function types in annotations](#function-types-in-annotations)
- [Common pitfalls](#common-pitfalls)

## Declaring a function
---
A named function is introduced with the `function` keyword followed by the name, a parameter list, an optional return annotation, and a body. The name is bound as a local when declared with `local function`; without `local` it becomes a global, which is almost never what you want.

```lua
local function greet(name: string): string
    return "hello, " .. name
end
```

**Breakdown**

- `local function name(...) ... end` declares a local function named `name`.
- `name: string` annotates the parameter; `: string` after the parameter list annotates the return type.
- `return` passes the value to the caller and ends the function.
- The body is the code between the closing parenthesis and `end`.

## Anonymous functions
---
A function expression produces a value without binding it to a name. Anonymous functions are used as callbacks, as immediately-invoked expressions, and as values in tables.

```lua
local add = function(a: number, b: number): number
    return a + b
end

LLEvents:on("touch_start", function(events)
    print("touched")
end)
```

**Breakdown**

- `function(a, b) ... end` is an expression producing a function value.
- Assigning it to `add` binds the value to a name.
- Passing it to `LLEvents:on` registers it as a callback; the function has no name of its own.

## Methods and the colon
---
A method is a function declared with a colon instead of a dot. The colon implicitly inserts a `self` parameter, and the colon at call time passes the receiver automatically.

```lua
local counter = { count = 0 }

function counter:increment()
    self.count += 1
end

counter:increment()
```

**Breakdown**

- `function counter:increment()` is equivalent to `function counter.increment(self)`; the `self` parameter is implicit.
- `counter:increment()` invokes with `counter` as `self`.
- Inside the body, `self` refers to the receiver.
- `counter.increment(counter)` and `counter:increment()` invoke the same function; the colon form passes the receiver automatically.
- Mixing the forms incorrectly is the most common method bug: `counter.increment()` without a receiver passes `nil` as `self`.

## Parameters and annotations
---
Parameters are positional. Each may be annotated; optional parameters use `T?` and default to `nil` when omitted. SLua has no default-value syntax in the parameter list; handle defaults inside the body.

```lua
local function greet(name: string, title: string?): string
    if title then
        return "hello, " .. title .. " " .. name
    end
    return "hello, " .. name
end

greet("alice")
greet("alice", "Dr.")
```

**Breakdown**

- `name: string` is required; omitting it passes `nil` and the annotation fails under strict mode.
- `title: string?` is optional; callers may pass it or omit it.
- `if title then` handles both `nil` (omitted) and any non-nil value (supplied).
- There is no `= default` in the parameter list; the default is written into the body.

## Multiple returns
---
A function may return any number of values. Callers capture them into matching variables, discard extras, or pack them into a table.

```lua
local function minmax(a: number, b: number): (number, number)
    if a < b then return a, b end
    return b, a
end

local lo, hi = minmax(3, 7)
local first = minmax(3, 7)
```

**Breakdown**

- `return a, b` returns two values.
- `local lo, hi = minmax(3, 7)` captures both.
- `local first = minmax(3, 7)` captures only the first; the second is discarded.
- When a call is not the last expression in a list, only its first value is used: `print(minmax(3, 7), "x")` prints only the first result followed by `"x"`.

## Varargs
---
A parameter written as `...` collects any number of trailing arguments into a vararg expression. Use `table.pack` to capture them as an array with a known count, or `select("#", ...)` to count them without materialising.

```lua
local function sum(...)
    local total = 0
    for _, v in ipairs(table.pack(...)) do
        total += v
    end
    return total
end

sum(1, 2, 3)
```

**Breakdown**

- `...` in the parameter list declares a variadic function.
- `...` in the body expands to the caller's arguments in order.
- `table.pack(...)` captures them into a table with an `n` field holding the count.
- `select("#", ...)` returns just the count; `select(i, ...)` returns the arguments from position `i` onward.

## Closures
---
A function value captures the locals in scope at the point of its creation. Captured variables remain alive for as long as the function value exists, even after the outer function returns.

```lua
local function counter()
    local n = 0
    return function(): number
        n += 1
        return n
    end
end

local next = counter()
print(next())    -- 1
print(next())    -- 2
```

**Breakdown**

- `counter()` returns a new function value.
- The returned function captures `n` from `counter`'s scope.
- Each call to `next()` mutates the same `n`; calling `counter()` again starts a fresh `n`.
- Two closures created from the same scope share the same captured variables; two closures from separate calls do not.

## Higher-order functions
---
A function may take another function as an argument or return one. The annotation for such a parameter is the callee’s call signature.

```lua
local function map<T, U>(arr: {T}, f: (T) -> U): {U}
    local out = {}
    for i, v in ipairs(arr) do
        out[i] = f(v)
    end
    return out
end

local doubled = map({1, 2, 3}, function(x) return x * 2 end)
```

**Breakdown**

- `f: (T) -> U` declares that `f` is a function from `T` to `U`.
- `map({1, 2, 3}, ...)` passes an anonymous function as `f`.
- `<T, U>` declares generic parameters instantiated at the call.
- The return type `{U}` is an array of `U` values.

## Recursion
---
A function may call itself. For a local function to recurse, use `local function name(...) ... end`, which binds the name before the body is compiled.

```lua
local function factorial(n: number): number
    if n <= 1 then return 1 end
    return n * factorial(n - 1)
end
```

**Breakdown**

- `local function name(...) ... end` makes `name` visible inside its own body, enabling recursion.
- `local name = function(...) ... end` does not; inside the body, `name` resolves to an outer variable of the same name or to `nil`, and the call fails.
- Deep recursion can overflow the stack; prefer an iterative form when the depth is unbounded.

## Function types in annotations
---
SLua has no bare `function` type annotation. A function type is written as a full call signature: a parenthesized argument list, an arrow `->`, and a return type. This is the only way to annotate a function value.

```lua
local cb: () -> () = function() end
local signed: (number, number) -> number = function(a, b) return a + b end
local variadic: (...any) -> ...any = function(...) return ... end
```

**Breakdown**

- `: () -> ()` declares a function that takes no arguments and returns nothing.
- `: (number, number) -> number` declares a function that takes two numbers and returns a number.
- `: (...any) -> ...any` accepts any call signature.
- There is no `: function` annotation; write the signature explicitly.

## Common pitfalls
---
A short list of things that behave differently from other languages, since SLua is not “Lua with features”; it is a language where these details are what they are.

```lua
local f = function() return 1, 2 end

print(f())              -- 1  2
print(f(), "x")         -- 1  x
print((f()))            -- 1
```

**Breakdown**

- `print(f())` expands both returns; the call is the last expression in the argument list.
- `print(f(), "x")` uses only `f()`’s first result, because it is not the last expression.
- `print((f()))` forces a single-value context with parentheses; only the first return is kept.
- The rule is: a call expands to multiple values only in a tail position of an expression list.
