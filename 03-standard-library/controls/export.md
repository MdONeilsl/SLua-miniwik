# export

The module export modifier. Marks a type alias, variable, or function as part of the module's public interface, making it available to code that requires the module. `export` is a contextual keyword: it is only a keyword at the top level of a module, before a declaration; anywhere else it is a plain identifier. This page lists every declaration that `export` can prefix, what each form makes visible, and the restrictions the parser and type checker enforce.

## Contents

- [Purpose](#purpose)
- [Exporting a type](#exporting-a-type)
- [Exporting a local variable](#exporting-a-local-variable)
- [Exporting a const variable](#exporting-a-const-variable)
- [Exporting a function](#exporting-a-function)
- [Exporting multiple bindings](#exporting-multiple-bindings)
- [Exporting a nested table](#exporting-a-nested-table)
- [Shadowing an exported name](#shadowing-an-exported-name)
- [Interaction with module return](#interaction-with-module-return)
- [Restriction: only at top level](#restriction-only-at-top-level)
- [Restriction: inside conditional blocks](#restriction-inside-conditional-blocks)

## Purpose

`export` turns a declaration into part of the module's public interface. Without it, a declaration is private to the module. With it, the declaration is added to a hidden export table that is frozen and returned when the module finishes loading, so importers can read it.

```lua
export type Point = { x: number, y: number }
export function distance(a: Point, b: Point): number
    local dx, dy = a.x - b.x, a.y - b.y
    return math.sqrt(dx * dx + dy * dy)
end
```

**Breakdown**

- `export type Point` makes the `Point` type visible to importers.
- `export function distance` makes the `distance` function visible to importers.
- Both are added to the module's export table at the point of declaration.
- Importers read them through the module's identifier after `require`.

## Exporting a type

The original and still most common form of `export`. A type alias prefixed with `export` becomes part of the module's type namespace, addressable by importers as `ModuleName.TypeName`.

```lua
export type Point = { x: number, y: number }
export type Pair<A, B> = { first: A, second: B }
export type PlayerId = number
```

**Breakdown**

- `export type Point` declares a type visible outside the module.
- `export type Pair<A, B>` exports a generic type alias; the generic parameters travel with the export.
- `export type PlayerId` exports a simple alias; importers can use `ModuleName.PlayerId` wherever a `number` is expected.
- Importers address these types as `Module.Point`, `Module.Pair<string, number>`, and `Module.PlayerId`.

## Exporting a local variable

A `local` variable prefixed with `export` becomes a value in the module's export table. The binding is still local to the module; the export table holds a reference to the value at the point the module returns.

```lua
export local version = "1.0"
export local settings: { [string]: any } = { debug = false }
```

**Breakdown**

- `export local version = "1.0"` adds `version` to the module's export table.
- `export local settings: { [string]: any }` exports a variable with an explicit type annotation.
- Within the module, both can be read and reassigned freely until the module returns.

## Exporting a const variable

A `const` binding prefixed with `export` is both immutable and exported. The exported value cannot be reassigned inside the module, and the export table entry cannot be replaced by importers either.

```lua
export const TAU = math.pi * 2
export const MAX_ITEMS = 10
```

**Breakdown**

- `export const TAU = math.pi * 2` exports a constant; no code, inside or outside the module, can reassign it.
- `export const MAX_ITEMS = 10` exports another constant.
- Exporting a `const` is the safest way to expose a configuration value; the compiler enforces immutability on both sides of the module boundary.

## Exporting a function

A function declaration prefixed with `export` is added to the export table as a callable value. Exported functions are implicitly `const`: they cannot be reassigned after declaration.

```lua
export function init(): ()
    print("module loaded")
end

export function add(a: number, b: number): number
    return a + b
end
```

**Breakdown**

- `export function init` exports a zero-argument function.
- `export function add` exports a two-argument function with a return type.
- Both are callable inside the module as ordinary locals and outside the module as `Module.init` and `Module.add`.
- Reassigning either function inside the module, as in `init = somethingElse`, is a compile error.

## Exporting multiple bindings

One `export` keyword can prefix a multi-assignment. Each name in the list becomes an entry in the export table.

```lua
export local a, b, c = 1, 2, 3
export local x, y = computeXY()
```

**Breakdown**

- `export local a, b, c = 1, 2, 3` exports three variables in one declaration.
- `export local x, y = computeXY()` exports two variables populated from a multi-return call.
- The same identifier cannot be exported twice; `export local foo = 1` followed by `export local foo = 2` is a parse error.

## Exporting a nested table

A table exported with `export local` is added to the export table by reference. The table itself is not frozen; its fields can be added and changed inside the module after declaration, and those changes are visible to importers because they share the same table.

```lua
export local triangle = {}
function triangle.draw(): ()
    print("drawing")
end
```

**Breakdown**

- `export local triangle = {}` exports an empty table.
- `function triangle.draw()` adds a `draw` method to that table after the export declaration.
- Importers see the `draw` method because the export table holds a reference to the same table, not a copy.
- The table is mutable; freezing it would require a separate call to `table.freeze`.

## Shadowing an exported name

Exporting a name does not prevent a later `local` declaration from shadowing it. The shadow is a separate binding; the exported binding keeps the value it had at the point of export.

```lua
export local fruit = "apple"

do
    local fruit = "banana"
    print(fruit)    -- banana
end

print(fruit)        -- apple
```

**Breakdown**

- The inner `local fruit = "banana"` shadows the exported `fruit` inside the block.
- The inner binding is not exported; it exists only inside the block.
- The exported binding retains `"apple"` and that is what importers see.
- A shadowing declaration with the same name as an exported one is legal; exporting the same name twice is not.

## Interaction with module return

A module may either use `export` declarations or return a table explicitly, but not both. Mixing the two is a compile error: once `export` is used, the compiler generates the return value, and a user-written `return` conflicts with it.

```lua
export function distance(a: Point, b: Point): number
    return 0
end

-- return { distance = distance }    -- compile error when export is used
```

**Breakdown**

- `export function distance` adds `distance` to the auto-generated export table.
- Writing `return { distance = distance }` at the end of the same module is rejected because the module already has an implicit return from the export machinery.
- To return a table explicitly, omit `export` on every declaration and write the `return` by hand; choose one style per module.

## Restriction: only at top level

`export` is valid only at the top level of a module. It is not valid inside a function body, a loop, or a block. The parser treats `export` as a contextual keyword and only recognises it before a top-level declaration.

```lua
-- local function f()
--     export local x = 1    -- compile error: not at top level
-- end
```

**Breakdown**

- `export` inside a function body is a syntax error.
- `export` inside a `do ... end` block is a syntax error.
- `export` inside a `for` or `while` loop is a syntax error.
- Only declarations written at column-zero top level may carry `export`.

## Restriction: inside conditional blocks

An `export` declaration may not appear inside an `if` branch or any other conditional block. The export table is built once when the module loads, not conditionally.

```lua
-- if condition then
--     export local bar = 1    -- compile error
-- end
```

**Breakdown**

- `export` inside an `if` block is a syntax error.
- To conditionally export a value, declare the variable with `export` unconditionally, then assign to it inside the `if`. The exported binding exists; its value is the one assigned at the point the module returns.
- This restriction exists so the export table has a fixed shape known at compile time.
