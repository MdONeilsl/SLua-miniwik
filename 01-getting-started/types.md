[README](README.md) · [syntax](syntax.md) · [control-flow](control-flow.md) · [functions](functions.md) · [scripts](scripts.md)

# Types

Every value in SLua has a type. This file lists them all: what each one represents, how to construct a value of that type, and where its methods are documented. Annotation syntax (`: T`, `T?`, `A | B`, `:: cast`) is covered in [syntax](syntax.md).

## Contents

- [nil](#nil)
- [boolean](#boolean)
- [number](#number)
- [integer](#integer)
- [string](#string)
- [table](#table)
- [function](#function)
- [thread](#thread)
- [buffer](#buffer)
- [vector](#vector)
- [quaternion](#quaternion)
- [uuid](#uuid)
- [Class types](#class-types)
- [any, unknown, never](#any-unknown-never)
- [typeof](#typeof)

## nil
---
The empty value. It is the only value of its type and represents absence: an uninitialised variable, a missing table field, a function returning nothing.

```lua
local x = nil
local t = {}
print(t.missing)     -- nil
```

**Breakdown**

- `local x = nil` binds `x` to the empty value.
- `t.missing` reads a field that was never set; the result is `nil`, not an error.
- Reading any unset local or field yields `nil`; only under strict mode does the compiler flag unset values before runtime.

## boolean
---
`true` and `false`. The result type of every comparison and of every logical operator when used in boolean context.

```lua
local flag = true
local same = (1 == 1)          -- true
local negated = not flag       -- false
```

**Breakdown**

- `true` and `false` are the only two boolean values.
- `==`, `~=`, `<`, `>`, `<=`, `>=` produce booleans.
- `not` flips a boolean.
- `and` and `or` return one of their operands, which may not be a boolean.

## number
---
A 64-bit IEEE-754 double-precision float. The type of every numeric literal containing a decimal point or an exponent, of every `/` and `^` result, and of the `math` library's outputs.

```lua
local f = 3.14
local half = 7 / 2       -- 3.5
local nan = 0 / 0        -- NaN
local inf = 1 / 0        -- +inf
```

**Breakdown**

- `3.14` is a float literal.
- `/` and `^` always produce a number, even when both operands are integers.
- `0/0` evaluates to NaN and `1/0` to infinity; neither raises an error.
- Use `math.isnan`, `math.isinf`, and `math.isfinite` to test for these values.

## integer
---
A 64-bit signed integer. The type of values produced by the `integer` library. Integer arithmetic wraps on overflow. SLua does not accept the `i` suffix on numeric literals; an integer is produced with `integer(...)` or `integer.create(...)`.

```lua
local a: integer = integer(42)
local b = integer.create(0xFF)           -- integer
local c = integer.create(7) // integer(2) -- integer 3
local big = integer.create(9223372036854775807)
```

**Breakdown**

- `integer(42)` produces an integer value from a number.
- `integer.create(0xFF)` produces an integer from a hexadecimal literal.
- `integer.create(9223372036854775807)` produces the maximum signed 64-bit integer.
- The `i` suffix (`42i`) is not supported by the SLua parser and raises a malformed-number error.
- Integer and number are distinct types; integers can be passed where numbers are expected, but not always the reverse.

## string
---
A sequence of bytes. Strings are immutable; every operation that "modifies" a string returns a new value. Long-bracket and quoted forms are covered in [syntax](syntax.md); the string library is documented in 03-standard-library/string.

```lua
local s = "hello"
local upper = string.upper(s)    -- "HELLO"
local joined = s .. " world"
local len = #s                   -- 5
```

**Breakdown**

- `"hello"` is a quoted string literal.
- `string.upper(s)` returns a new string; `s` is unchanged.
- `..` produces a new string from two operands.
- `#s` returns the number of bytes, not the number of grapheme clusters.

## table
---
The only compound structure. A table is a collection of key-value pairs where keys can be any value except `nil` and NaN. Arrays are tables with consecutive integer keys starting at 1. Construction syntax is covered in [syntax](syntax.md); methods, metatables, and iterators are documented in 03-standard-library/table.

```lua
local arr = { 10, 20, 30 }
local rec = { name = "alice", score = 42 }
local grid = { {1, 2}, {3, 4} }
```

**Breakdown**

- `{10, 20, 30}` is an array-shaped table.
- `{name = "alice", score = 42}` is a record-shaped table.
- `{ {1, 2}, {3, 4} }` is a table of tables.
- Tables are the only reference type whose identity is observable: two tables with equal contents are still distinct unless compared through a custom metamethod.

## function
---
First-class. A function is a value that can be stored, passed as an argument, and returned. Every function has a call signature and a body; callers use the signature. Declaration forms, closures, and recursion are covered in [functions](functions.md).

```lua
local add = function(a: number, b: number): number
    return a + b
end

local result = add(1, 2)
```

**Breakdown**

- `function(a, b) ... end` is a function expression producing a value.
- Assigning it to `add` binds the value to a name.
- `add(1, 2)` invokes the function value; the parentheses are the invocation operator.

## thread
---
A coroutine. Created with `coroutine.create` and resumed with `coroutine.resume`. A thread runs cooperatively and yields with `coroutine.yield`. The library is documented in 03-standard-library/coroutine.

```lua
local co = coroutine.create(function()
    coroutine.yield(1)
    coroutine.yield(2)
end)
```

**Breakdown**

- `coroutine.create(f)` returns a thread whose body is `f`.
- The thread does not run until `coroutine.resume(co)` is called.
- Each `coroutine.yield(v)` pauses the thread and passes `v` back to the resumer.

## buffer
---
A fixed-size, mutable binary region. Created with `buffer.create`. Buffers are the only type that supports in-place byte modification. The library is documented in 03-standard-library/buffer.

```lua
local b = buffer.create(16)
buffer.writeu8(b, 0, 255)
```

**Breakdown**

- `buffer.create(16)` allocates a 16-byte buffer filled with zeros.
- `buffer.writeu8(b, 0, 255)` writes byte value 255 at offset 0.
- `buffer.tostring(b)` converts to a string; `buffer.fromstring(s)` creates a buffer from a string.

## vector
---
A three-component float structure from the standard library. Used for positions, directions, velocities, and colors. Constructed with `vector(x, y, z)`; components are read and written through `.x`, `.y`, `.z`. The library is documented in 03-standard-library/vector.

```lua
local pos = vector(1, 2, 3)
local dir = vector(0, 1, 0)
```

**Breakdown**

- `vector(x, y, z)` constructs a vector.
- `vector.zero` and `vector.one` are the standard constants.
- Components are accessible via `.x`, `.y`, `.z`.
- Vectors support component-wise addition, subtraction, and scalar multiplication with standard operators.

## quaternion
---
A four-component float structure representing a rotation. `rotation` is an alias for `quaternion`; the two names refer to the same type and are interchangeable in annotations, casts, and function signatures. The library is documented in 03-standard-library/modules/quaternion.

```lua
local q = quaternion(0, 0, 0, 1)
local r: rotation = q
```

**Breakdown**

- `quaternion(x, y, z, s)` constructs a quaternion; `s` is the scalar component.
- `quaternion.identity` is the identity rotation.
- `rotation` and `quaternion` are the same type; annotating with one and passing the other is legal.

## uuid
---
A 128-bit identifier from the standard library. Used for agent, object, and inventory keys. The library is documented in 03-standard-library/uuid.

```lua
local id = uuid("A822FF2B-FF02-461D-B45D-DCD10A2DE0C2")
```

**Breakdown**

- `uuid(s)` parses a 36-character string into a uuid; invalid input raises.
- `id.bytes` returns the raw 16-byte representation.
- `id.istruthy` returns false for the null uuid and true otherwise.

## Class types
---
Some names refer to instances of classes defined by the environment. `LLEvents`, `LLTimers`, `DetectedEvent`, and `PrimParamSetterType` are classes; their values have methods documented in 04-ll-library/event and 03-standard-library/llprim. The example below uses `LLEvents:on`, whose signature is `on(self, event: LLEventName, callback: LLEventHandler) -> LLEventHandler`.

```lua
local handler = LLEvents:on("touch_start", function(events)
    print("touched")
end)
```

**Breakdown**

- `LLEvents` is a singleton value of class `LLEvents`.
- `LLEvents:on(...)` invokes the `on` method on that singleton; the colon passes `LLEvents` as `self`.
- `"touch_start"` is the event name; the valid set is defined by `LLEventName`.
- The callback receives the event arguments as a table; `events` is bound to it.
- `handler` has type `LLEventHandler`, a function alias defined by the environment.

## any, unknown, never
---
Three special types used in annotations and generics. `any` disables checking; `unknown` accepts anything but requires a cast before use; `never` has no values and is the return type of functions that never return.

```lua
local a: any = anything
local u: unknown = anything
local n: never = error("this never returns")
```

**Breakdown**

- `any` accepts every value without type checking.
- `unknown` accepts every value but must be cast or narrowed before use.
- `never` is the return type of functions that never return; no value has type `never`.

## typeof
---
`typeof(v)` returns the runtime type name of a value as a string. Unlike `type`, it reports SLua-specific types by their real names.

```lua
print(typeof(1))                -- "number"
print(typeof("x"))              -- "string"
print(typeof(vector(1, 2, 3)))  -- "vector"
print(typeof(nil))              -- "nil"
```

**Breakdown**

- `typeof(v)` returns the name of `v`'s type.
- For standard types it returns the same names used in annotations.
- For object types like vector, quaternion, and uuid it returns their specific names.
