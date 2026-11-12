# function

The function declaration keyword. Introduces a named or anonymous function value, opening a block whose body executes when the function is called. `function` is used in three syntactic forms: as a statement that binds a name, as an expression that produces a value, and as a method declaration using a colon. Each form opens a body that closes with `end`. This page lists every syntactic form, the parameter rules, the return rules, and the interactions with `local`, `const`, and `export`.

## Contents

- [Purpose](#purpose)
- [Named function statement](#named-function-statement)
- [Local function declaration](#local-function-declaration)
- [Const function declaration](#const-function-declaration)
- [Exported function declaration](#exported-function-declaration)
- [Anonymous function expression](#anonymous-function-expression)
- [Method declaration with colon](#method-declaration-with-colon)
- [Parameters](#parameters)
- [Return](#return)
- [Type annotations](#type-annotations)
- [Recursion and self-reference](#recursion-and-self-reference)
- [Function as a table field](#function-as-a-table-field)
- [Restrictions](#restrictions)

## Purpose

`function` introduces a function value. Every use of the keyword opens a block whose body runs when the function is invoked and closes with `end`. The three syntactic roles differ only in how the resulting value is bound: a statement binds it to a name, an expression leaves it as the value of an expression, and a method declaration binds it to a table field with an implicit `self` parameter.

```lua
function greet(name: string): string
    return "hello, " .. name
end

local add = function(a: number, b: number): number
    return a + b
end
```

**Breakdown**

- `function greet(...)` is a named statement form.
- `local add = function(...)` uses the anonymous expression form, then binds the result to `add`.
- Both open a body with the parameter list and close it with `end`.

## Named function statement

A `function` statement at the top level or in a block binds the function to a name. Without `local`, the name becomes a global; with `local` (as in the next section), the name becomes a local. Globals are almost never appropriate in SLua scripts; always qualify with `local` unless you have a specific reason not to.

```lua
function hello(): ()
    print("hello")
end
```

**Breakdown**

- `function hello(): ()` declares a global function named `hello`.
- The body prints `"hello"` when called.
- The empty return type `()` marks a function that returns nothing; the annotation is optional.
- Globals persist between script loads on the same object; use `local` instead.

## Local function declaration

`local function name(...) ... end` declares a function bound to a local variable. Unlike `local name = function(...) ... end`, the local form binds the name **before** the body is compiled, which makes recursion work without extra setup.

```lua
local function factorial(n: number): number
    if n <= 1 then return 1 end
    return n * factorial(n - 1)
end
```

**Breakdown**

- `local function factorial(...)` binds `factorial` as a local and makes it visible inside its own body.
- The recursive call `factorial(n - 1)` resolves to the same function.
- Using `local factorial = function(...)` instead would fail: inside the body, `factorial` would resolve to an outer variable or to `nil`.

## Const function declaration

`local const function name(...) ... end` declares a local function whose binding cannot be reassigned. The function is otherwise identical to `local function`.

```lua
local const function distance(a: vector, b: vector): number
    return vector.magnitude(a - b)
end
```

**Breakdown**

- `local const function distance(...)` binds `distance` as an immutable local.
- Calling `distance(...)` works exactly as with `local function`.
- Reassigning `distance = otherFn` later is a compile error.

## Exported function declaration

`export function name(...) ... end` at the top level of a module adds the function to the module's public export table. Exported functions are implicitly const.

```lua
export function clamp(n: number, lo: number, hi: number): number
    if n < lo then return lo end
    if n > hi then return hi end
    return n
end
```

**Breakdown**

- `export function clamp(...)` declares a function and adds it to the export table.
- Importers address it as `Module.clamp(...)`.
- The binding is implicitly `const`; reassigning `clamp` inside the module is a compile error.

## Anonymous function expression

The `function` keyword may appear anywhere an expression is expected, producing a function value that is not bound to a name. This is the form used for callbacks, immediately-invoked expressions, and table entries.

```lua
local double = function(x: number): number
    return x * 2
end

LLEvents:on("touch_start", function(events)
    print("touched")
end)
```

**Breakdown**

- `function(x: number) ... end` produces a function value.
- `local double = function(...)` binds the value to `double`.
- `LLEvents:on(..., function(events) ... end)` passes the value as an argument.
- An anonymous function value that is never stored or passed is immediately discarded.

## Method declaration with colon

`function table:name(...) ... end` declares a method on a table. The colon inserts an implicit `self` parameter, so the body sees the receiver as `self` and callers use `table:name(...)`.

```lua
local counter = { count = 0 }

function counter:increment(): ()
    self.count += 1
end

counter:increment()
```

**Breakdown**

- `function counter:increment(...)` is equivalent to `function counter.increment(self)` with `self` implicit.
- `counter:increment()` passes `counter` as `self`.
- Inside the body, `self.count` reads the receiver's field.
- The dot form `counter.increment()` without a receiver passes `nil` as `self` and the body raises.

## Parameters

The parameter list between parentheses is a comma-separated sequence of names, each optionally annotated with a type. Three special forms exist: no parameters, optional parameters (annotated with `?`), and a trailing `...` vararg.

```lua
local function none(): ()
end

local function one(a: number): ()
end

local function optional(a: number, b: string?): ()
end

local function variadic(a: number, ...: any): ()
end
```

**Breakdown**

- `()` declares a function with no parameters.
- `(a: number)` declares one required parameter.
- `(a: number, b: string?)` declares one required and one optional parameter; callers may omit `b`.
- `(a: number, ...: any)` declares a required parameter followed by a vararg.
- The vararg must be the last item in the parameter list; placing anything after it is a syntax error.

## Return

Every function body is a block, and the `return` statement ends the function early, passing values back to the caller. A function without any `return` returns no values.

```lua
local function classify(n: number): string
    if n > 0 then
        return "positive"
    elseif n < 0 then
        return "negative"
    end
    return "zero"
end
```

**Breakdown**

- Each `return` ends the function and passes its value to the caller.
- The final `return "zero"` runs only when neither earlier branch matched.
- A function that reaches `end` without a `return` returns no values.

## Type annotations

The parameter list and the return type are both optional. When present, the type checker verifies them under strict mode; when absent, the function's signature is inferred as `(...any) -> ...any`.

```lua
local function add(a: number, b: number): number
    return a + b
end

local function passthrough(...: any): ...any
    return ...
end
```

**Breakdown**

- `(a: number, b: number): number` annotates both parameters and the return.
- `(...: any): ...any` annotates a vararg and a vararg return.
- The absence of a return annotation is equivalent to `: any`, not `: ()`.

## Recursion and self-reference

A function may call itself. For `local function name(...) ... end`, the name is visible inside the body from the start. For `local name = function(...) ... end`, the name is not bound until after the expression is evaluated, so recursion from inside the body does not work unless the function captures a table field or a forward declaration.

```lua
local function factorial(n: number): number
    if n <= 1 then return 1 end
    return n * factorial(n - 1)
end
```

**Breakdown**

- `local function factorial` binds the name before the body.
- The recursive call `factorial(n - 1)` resolves to the same function.
- Deep recursion can overflow the stack; SLua does not perform tail-call optimisation in all cases.

## Function as a table field

A function may be assigned to a table field, either with dot syntax inside a table constructor or by assignment after construction. A function stored in a table is a method when called with a colon and a plain function value when called with a dot.

```lua
local util = {
    double = function(n: number): number
        return n * 2
    end,
}

util.triple = function(n: number): number
    return n * 3
end

print(util.double(4))    -- 8
print(util.triple(4))    -- 12
```

**Breakdown**

- `util.double` is created in the table constructor.
- `util.triple` is added by assignment afterward.
- Both are called with dot syntax because neither expects `self`.
- Assigning a function to a table field is the standard way to build modules and record-style objects.

## Restrictions

`function` requires `end` to close the body. The parameter list must be present and parenthesized. A `function` expression cannot appear as a statement on its own; it is only valid where an expression is expected, or in the statement forms that bind it to a name.

```lua
-- function(a, b) return a + b end     -- compile error: expression used as statement
-- local f = function(a, b)             -- compile error: missing end
```

**Breakdown**

- An anonymous `function(...)` used as a statement is rejected; wrap it in a `local` assignment or pass it as an argument.
- An anonymous function without `end` is rejected at the point where the parser expects `end`.
- The parameter list is mandatory; `function() end` is valid but `function end` is not.
