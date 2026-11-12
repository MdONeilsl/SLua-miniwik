# write

The write-only property modifier in type annotations. Marks a table field or indexer as writable but not readable, so that any read of it is rejected by the type checker. `write` is a contextual keyword: it is only a keyword inside a table type, immediately before a property or indexer declaration; anywhere else it is a plain identifier. This page lists every position where `write` is valid, the semantics it introduces, and the interaction with `read`.

## Contents

- [Purpose](#purpose)
- [Write-only properties](#write-only-properties)
- [Write-only indexers](#write-only-indexers)
- [Arrays and the shorthand form](#arrays-and-the-shorthand-form)
- [Mixing read and write](#mixing-read-and-write)
- [Contravariance](#contravariance)
- [write as a property name](#write-as-a-property-name)
- [Use cases](#use-cases)
- [Interaction with table.freeze](#interaction-with-tablefreeze)
- [Restrictions](#restrictions)

## Purpose

`write` annotates a table field as writable. Values of that type can be assigned through the field, but the type checker rejects any attempt to read it. It is a compile-time guarantee only: at runtime, the underlying table still holds a value and reading it succeeds unless the value itself is `nil`.

```lua
type Sink = { write value: number }

local s: Sink = {}
s.value = 10        -- ok
print(s.value)      -- type error: value is write-only
```

**Breakdown**

- `type Sink = { write value: number }` declares a type whose `value` field is writable.
- `s.value = 10` assigns to the field; this is allowed.
- `print(s.value)` is rejected by the type checker because `value` is marked `write`.
- The runtime table still holds `10`; the constraint is on the type, not the value.

## Write-only properties

The basic form: `write name: Type` inside a table type. Any value of that type exposes `name` for assignment and blocks reading from it. Multiple properties may be declared `write` in the same type.

```lua
type Loader = {
    write filename: string,
    write size: number,
}

local load: Loader = {}
load.filename = "data.txt"    -- ok
load.size = 1024              -- ok
local s = load.size           -- type error: size is write-only
```

**Breakdown**

- Both `filename` and `size` are declared `write`.
- Writing either field is allowed.
- Reading either field is rejected by the type checker.
- The underlying table holds the values; they can be inspected at runtime only through a cast or through a value of a read-enabled type.

## Write-only indexers

`write` applies to indexers as well. `{ write [K]: V }` declares a map whose entries can be assigned but not read. The indexer form accepts any key type and any value type.

```lua
type Sink<K, V> = { write [K]: V }

local sink: Sink<string, number> = {}
sink["count"] = 5    -- ok
print(sink["count"]) -- type error: indexer is write-only
```

**Breakdown**

- `{ write [K]: V }` declares a write-only indexer.
- `sink["count"] = 5` assigns an entry; this is allowed.
- `print(sink["count"])` is rejected by the type checker.
- The same form works for `Sink<string, any>`, `Sink<number, string>`, and so on.

## Arrays and the shorthand form

For array types, `write` can be applied without an explicit key. The form `{ write V }` declares an array of `V` whose elements are write-only.

```lua
type WriteAnimals = { write Animal }

local a: WriteAnimals = {}
a[1] = dog            -- ok
a[2] = cat            -- ok
local first = a[1]    -- type error: array is write-only
```

**Breakdown**

- `{ write Animal }` is shorthand for `{ write [number]: Animal }`.
- Assigning to `a[1]` or `a[2]` is allowed.
- Reading from `a[1]` is rejected.
- The shorthand is convenient for annotated parameter types where the function only appends, never inspects.

## Mixing read and write

A field may be declared both `read` and `write`, potentially with different types. The `read` side is what callers see when they read; the `write` side is what callers must supply when they write. The two may differ, though mixing them is discouraged.

```lua
type Foo = {
    read p: Animal,
    write p: Dog,
}
```

**Breakdown**

- `read p: Animal` says the field returns an `Animal`.
- `write p: Dog` says the field accepts only a `Dog`.
- A value of type `Foo` can be read as `Animal` and written as `Dog`.
- The two annotations coexist on the same property; each contributes half of the field's semantics.

## Contravariance

Write-only properties are contravariant: if `T` is a subtype of `U`, then `{ write p: U }` is a subtype of `{ write p: T }`. This means a type that accepts a broader set of writes can be used wherever a type that accepts a narrower set is expected. Read-only and read-write properties do not have this property.

```lua
type AnimalSink = { write a: Animal }
type DogSink = { write a: Dog }

local function feed(d: DogSink): ()
    d.a = dog
end

local as: AnimalSink = {}
feed(as)    -- ok: AnimalSink is a subtype of DogSink
```

**Breakdown**

- `AnimalSink` accepts any `Animal` for `a`.
- `DogSink` accepts only a `Dog` for `a`.
- Every `Dog` is an `Animal`, so any value that accepts an `Animal` accepts a `Dog`.
- `AnimalSink` is therefore a subtype of `DogSink`, and `feed(as)` is accepted.
- The contravariance of `write` makes this substitution safe: `feed` only writes, never reads.

## write as a property name

Because `write` is contextual, it remains a valid property name. A property literally called `write` is written as `write: Type`, not `write write: Type`. The distinction is the colon: a modifier is followed by another identifier, whereas a property is followed by a colon.

```lua
type Writer = { write: (string) -> () }

local w: Writer = { write = function(s) print(s) end }
w.write("hello")    -- hello
```

**Breakdown**

- `write: (string) -> ()` declares a property named `write` whose value is a function.
- `w.write("hello")` reads the property and calls the function.
- Writing `write write: (string) -> ()` would declare a write-only property named `write`; the single-`write` form is the property.
- This dual role is why `write` cannot be a reserved keyword.

## Use cases

The primary use of `write` is to model a channel that carries values in one direction only: a queue producer, a logger, a callback slot. Such a type lets the implementation write entries while hiding the stored data from the caller, and lets the type checker guarantee that no caller ever inspects the entries directly.

```lua
type Logger = { write log: string }

local function setup(logger: Logger): ()
    logger.log = "started"
    logger.log = "ready"
end
```

**Breakdown**

- `Logger` accepts writes to `log` and nothing else.
- `setup` can append messages but cannot read them back.
- The caller of `setup` passes a table whose `log` field the function appends to.
- The type checker guarantees that `setup` does not read `log`, so the implementation can enforce the intended access pattern.

## Interaction with table.freeze

`write` is a type-system guarantee; `table.freeze` is a runtime guarantee. They conflict when combined: a frozen table rejects all writes at runtime, so a value of a write-only type that is also frozen cannot be written to in practice, even though the type permits it.

```lua
type Logger = { write log: string }

local logger: Logger = table.freeze({})
logger.log = "started"    -- type ok, runtime error: table is frozen
```

**Breakdown**

- `write log: string` permits the assignment `logger.log = "started"` at compile time.
- `table.freeze` blocks the same assignment at runtime.
- The type checker does not know about `table.freeze`; the mismatch is only caught at runtime.
- Do not combine `write` fields with frozen tables unless the intent is to write zero times.

## Restrictions

`write` is only valid inside a table type, immediately before a property name or indexer. It cannot appear in value declarations, function signatures outside of a table type, or as a statement on its own. A field may have at most one `write` annotation; declaring the same field `write` twice is an error.

```lua
-- local write x = 1         -- error: write is not a declaration modifier
-- type T = { write x: number, write x: string }    -- error: duplicate write
-- type T = { x: number, write x: string }          -- error: mixed unannotated and write
```

**Breakdown**

- `write` before a `local` declaration is rejected.
- Two `write` annotations on the same field are rejected.
- A field declared both without a modifier and with `write` is rejected; use one form or the other.
- The restriction mirrors `read`: each field may have at most one `read` and at most one `write` annotation.

