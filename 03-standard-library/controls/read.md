# read

The read-only property modifier in type annotations. Marks a table field or indexer as readable but not writable, so that any assignment to it is rejected by the type checker. `read` is a contextual keyword: it is only a keyword inside a table type, immediately before a property or indexer declaration; anywhere else it is a plain identifier. This page lists every position where `read` is valid, the semantics it introduces, and the interaction with `write`.

## Contents

- [Purpose](#purpose)
- [Read-only properties](#read-only-properties)
- [Read-only indexers](#read-only-indexers)
- [Arrays and the shorthand form](#arrays-and-the-shorthand-form)
- [Mixing read and write](#mixing-read-and-write)
- [Covariance](#covariance)
- [read as a property name](#read-as-a-property-name)
- [Interaction with table.freeze](#interaction-with-tablefreeze)
- [Restrictions](#restrictions)

## Purpose

`read` annotates a table field as readable. Values of that type can be read through the field, but the type checker rejects any attempt to assign to it. It is a compile-time guarantee only: at runtime, nothing stops a script from writing to the underlying table unless the table is also frozen.

```lua
type ReadOnly = { read x: number }

local v: ReadOnly = { x = 10 }
print(v.x)          -- 10
v.x = 20            -- type error: x is read-only
```

**Breakdown**

- `type ReadOnly = { read x: number }` declares a type whose `x` field is readable.
- `print(v.x)` reads the field; this is allowed.
- `v.x = 20` is rejected by the type checker because `x` is marked `read`.
- The runtime value `{ x = 10 }` is an ordinary table; `read` is a static constraint, not a runtime lock.

## Read-only properties

The basic form: `read name: Type` inside a table type. Any value of that type exposes `name` for reading and blocks assignment to it. Multiple properties may be declared `read` in the same type.

```lua
type Point = {
    read x: number,
    read y: number,
}

local p: Point = { x = 1, y = 2 }
local a = p.x + p.y    -- ok
p.x = 10               -- type error
```

**Breakdown**

- Both `x` and `y` are declared `read`.
- Reading either field is allowed.
- Writing either field is rejected by the type checker.
- The underlying table still holds the fields; the constraint is on the type, not the value.

## Read-only indexers

`read` applies to indexers as well. `{ read [K]: V }` declares a map whose entries can be read but not assigned. The indexer form accepts any key type and any value type.

```lua
type ReadOnlyMap<K, V> = { read [K]: V }

local m: ReadOnlyMap<string, number> = { count = 5 }
print(m["count"])    -- 5
m["count"] = 10      -- type error: indexer is read-only
```

**Breakdown**

- `{ read [K]: V }` declares a read-only indexer.
- `m["count"]` reads an entry; this is allowed.
- `m["count"] = 10` is rejected by the type checker.
- The same form works for `ReadOnlyMap<string, any>`, `ReadOnlyMap<number, string>`, and so on.

## Arrays and the shorthand form

For array types, `read` can be applied without an explicit key. The form `{ read V }` declares an array of `V` whose elements are read-only.

```lua
type ReadAnimals = { read Animal }

local a: ReadAnimals = { dog, cat }
local first = a[1]      -- ok
a[1] = bird             -- type error: array is read-only
```

**Breakdown**

- `{ read Animal }` is shorthand for `{ read [number]: Animal }`.
- Reading `a[1]` is allowed.
- Assigning to `a[1]` is rejected.
- The shorthand is convenient for annotated return types where the array is meant to be inspected, not modified.

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

## Covariance

Read-only properties are covariant: if `T` is a subtype of `U`, then `{ read p: T }` is a subtype of `{ read p: U }`. This means a type with a narrower read-only property can be used wherever a type with a broader read-only property is expected. Write-only and read-write properties do not have this property.

```lua
type Animal = { read name: string }
type Dog = { read name: string, read breed: string }

local function describe(a: Animal): ()
    print(a.name)
end

local d: Dog = { name = "Rex", breed = "Husky" }
describe(d)    -- ok: Dog is a subtype of Animal
```

**Breakdown**

- `Dog` has all the fields of `Animal` plus `breed`.
- Any `Dog` value can be passed where an `Animal` is expected because every field `Animal` promises to have is present in `Dog`.
- The covariance of `read` makes this substitution safe: `describe` only reads, never writes.

## read as a property name

Because `read` is contextual, it remains a valid property name. A property literally called `read` is written as `read: Type`, not `read read: Type`. The distinction is the colon: a modifier is followed by another identifier, whereas a property is followed by a colon.

```lua
type Reader = { read: () -> number }

local r: Reader = { read = function() return 42 end }
local n = r.read()    -- 42
```

**Breakdown**

- `read: () -> number` declares a property named `read` whose value is a function.
- `r.read()` reads the property and calls the function.
- Writing `read read: () -> number` would declare a read-only property named `read`; the single-`read` form is the property.
- This dual role is why `read` cannot be a reserved keyword.

## Interaction with table.freeze

`read` is a type-system guarantee; `table.freeze` is a runtime guarantee. The two are complementary. A field marked `read` is protected from writes at compile time, and a frozen table is protected from writes at runtime, including from code that ignored the type annotation.

```lua
type Config = { read debug: boolean }

local cfg: Config = table.freeze({ debug = false })
print(cfg.debug)      -- false
cfg.debug = true      -- type error, and a runtime error if forced
```

**Breakdown**

- `read debug: boolean` blocks `cfg.debug = ...` at compile time.
- `table.freeze` blocks the same assignment at runtime.
- Using both closes the type-checking gap: code that casts away the type annotation still cannot write.
- `table.freeze` is shallow; nested tables need their own freeze calls.

## Restrictions

`read` is only valid inside a table type, immediately before a property name or indexer. It cannot appear in value declarations, function signatures outside of a table type, or as a statement on its own. A field may have at most one `read` annotation; declaring the same field `read` twice is an error.

```lua
-- local read x = 1          -- error: read is not a declaration modifier
-- type T = { read x: number, read x: string }    -- error: duplicate read
-- type T = { x: number, read x: string }         -- error: mixed unannotated and read
```

**Breakdown**

- `read` before a `local` declaration is rejected.
- Two `read` annotations on the same field are rejected.
- A field declared both without a modifier and with `read` is rejected; use one form or the other.
- The restriction mirrors `write`: each field may have at most one `read` and at most one `write` annotation.

