[README](README.md) · [types](types.md) · [control-flow](control-flow.md) · [functions](functions.md) · [scripts](scripts.md)

# Syntax

The rules of writing SLua source text: how to form comments, name variables, write literals, use operators, construct tables, and annotate types. Every other document in this miniwik assumes these rules. Read this once; you should not need to come back unless you forget an edge case.

## Contents

- [Comments](#comments)
- [Variables](#variables)
- [Literals](#literals)
- [Operators](#operators)
- [Table constructors](#table-constructors)
- [Type annotations](#type-annotations)
- [Type aliases and generics](#type-aliases-and-generics)
- [Type casts](#type-casts)

## Comments
---
Two forms. A single-line comment begins with two hyphens and runs to the end of the line. A block comment begins with two hyphens and two opening square brackets, ends with two closing square brackets, and can span multiple lines. Both forms can nest when their delimiters differ.

```lua
-- single-line comment

--[[
    multi-line
    block comment
]]

--[==[
    body may contain ]] when the delimiter uses more equals signs
]==]
```

**Breakdown**

- `--` begins a single-line comment. Everything after it on the same line is ignored.
- `--[[ ... ]]` is a block comment. Any number of equals signs may be inserted between the brackets to allow the body to contain `]]` or `[[`.
- Block comments nest only when their delimiters differ; identical delimiters close the nearest matching block.

## Variables
---
A variable is introduced with `local` and is visible from that line to the end of the enclosing block. A constant is introduced with `local const`; the compiler rejects any assignment after declaration.

```lua
local count = 0
local name: string = "player"

local const MAX_HP = 100
local const GREETING: string = "hello"
```

**Breakdown**

- `local count = 0` declares a mutable local `count` initialised to `0`. Type is inferred as `number`.
- `local name: string = "player"` declares a local with an explicit annotation.
- `local const MAX_HP = 100` declares a constant; any later assignment is a compile error.
- `local const GREETING: string = "hello"` combines `const` with an explicit type.

## Literals
---
SLua has literals for numbers, strings, booleans, and `nil`. Numbers may be written in decimal, hexadecimal, or binary; underscores in numeric literals are ignored. All numeric literals without a decimal point or exponent are floats unless produced through the `integer` library. The `i` suffix on numeric literals is not supported.

```lua
local n   = 42
local f   = 3.14
local e   = 1e-9
local hex = 0xFF
local bin = 0b1010
local big = 1_000_000

local s1 = "double"
local s2 = 'single'
local s3 = [[long
bracket
string]]
local s4 = [==[body can contain ]] inside]==]
local s5 `dynamic {hex} casting`

local t = true
local nilValue = nil

local max = integer.create(9223372036854775807)
```

**Breakdown**

- `42`, `0xFF`, `0b1010`, `1_000_000` are numeric literals; underscores are ignored.
- `3.14` and `1e-9` are float literals.
- `42`, `0xFF`, `0b1010`, `1_000_000` are floats in SLua; to obtain an integer, use `integer(n)` or `integer.create(n)`.
- `integer.create(9223372036854775807)` produces the maximum signed 64-bit integer. The `i` suffix (`9223372036854775807i`) is not supported and raises a malformed-number error.
- `"double"` and `'single'` are quoted strings; both support the standard escape sequences `\n`, `\t`, `\"`, `\\`, and `\xNN`.
- `[[...]]` is a long-bracket string: it preserves newlines and treats every character literally except the closing bracket.
- `[==[...]==]` extends the delimiters with equals signs so the body may contain `]]`.
- `true` and `nil` are the boolean and empty literals.

## Operators
---
SLua uses the standard Lua operator set: arithmetic, comparison, logical, concatenation, and length. `/` always returns a float; `//` is floor division. There are no bitwise operators; use the `bit32` or `integer` libraries for those.

```lua
local sum      = 1 + 2
local quotient = 7 / 2          -- 3.5
local intdiv   = 7 // 2         -- 3
local modulo   = 7 % 2          -- 1
local power    = 2 ^ 10         -- 1024.0

local eq  = 1 == 1
local neq = 1 ~= 2
local lt  = 1 <  2
local le  = 1 <= 2

local a = true and false        -- false
local b = true or  false        -- true
local c = not true              -- false

local concat = "a" .. "b"       -- "ab"
local length = #"hello"         -- 5
```

**Breakdown**

- `/` always returns a float; `//` performs integer (floor) division.
- `%` returns the remainder with the sign of the divisor.
- `^` is exponentiation and always returns a float.
- `==` and `~=` are the only equality operators; they compare by value for primitives and by reference for tables.
- `and`, `or`, `not` return one of their operands, not necessarily a boolean.
- `..` concatenates strings and numbers; both operands must be concatenable.
- `#` returns the number of bytes in a string, or the array boundary of a table.
- Precedence follows Lua: `^` highest, then unary operators, then `* / // %`, then `+ -`, then `..`, then comparisons, then `and`, then `or`.

## Table constructors
---
Tables are the only compound structure. A constructor is an expression that produces a new table. Fields may be positional, named, or both; positional fields fill indices starting at 1.

```lua
local empty = {}
local array = { 10, 20, 30 }
local record = { name = "alice", score = 42 }
local mixed = { "first", "second", label = "mixed" }
local nested = { {1, 2}, {3, 4} }
```

**Breakdown**

- `{}` creates an empty table.
- `{10, 20, 30}` fills indices 1, 2, and 3.
- `{name = "alice", score = 42}` fills string keys.
- Mixed constructors fill array indices for positional entries and string keys for named entries; the two coexist.
- `{ {1, 2}, {3, 4} }` is the standard way to represent a matrix or a list of records.

## Type annotations
---
Under strict mode every local, parameter, and return can carry a type annotation. The annotation follows the identifier and a colon. Optional and union types extend the base syntax.

```lua
local count: number = 0
local name: string? = nil                -- optional
local flag: boolean = true

local function add(a: number, b: number): number
    return a + b
end

local function pick(useString: boolean): string | number
    if useString then return "yes" end
    return 1
end
```

**Breakdown**

- `: number`, `: string`, `: boolean` annotate a value with a single type.
- `: string?` annotates an optional type: the value is either a string or `nil`.
- `: string | number` annotates a union: the value is one of the listed types.
- Parameter and return annotations follow the same rules as local annotations.
- A function's return annotation follows the parameter list and a colon.

## Type aliases and generics
---
A named type is introduced with `type`; `export type` makes it visible outside the current module. Generic parameters are written in angle brackets after the name.

```lua
export type Point = { x: number, y: number }
export type Pair<A, B> = { first: A, second: B }
export type PlayerId = number

local origin: Point = { x = 0, y = 0 }
local pair: Pair<string, number> = { first = "a", second = 1 }
```

**Breakdown**

- `type Name = ...` declares a local type alias.
- `export type Name = ...` declares a type visible to importers of the module.
- `<A, B>` declares generic parameters usable in the body of the alias.
- `PlayerId` and `number` are interchangeable wherever `PlayerId` is in scope.
- Instantiation uses `<string, number>` after the alias name.

## Type casts
---
`::` asserts a type at compile time. The cast has no runtime cost; it only informs the compiler.

```lua
local raw = fetchData()          -- type unknown
local player = raw :: Player
```

**Breakdown**

- `raw :: Player` asserts that `raw` is of type `Player`.
- The cast is erased at compile time; if the runtime value is not actually a `Player`, the failure surfaces at first misuse, not at the cast.
