# metamethods

Operator and special-behaviour metamethods for tables.

## `__add`

Defines behavior for the addition (+) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand of the addition. |
| `right` | `any` | Right operand of the addition. |

**Returns:** `any`

## `__call`

Called when the table or object is called as if it were a function.

```lua
<A..., R...>(self: {}, A...) -> R...
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Table being invoked. |
| `...` | `A...` | Arguments passed to the call. |

**Returns:** `R...`

## `__concat`

Defines behavior for the concatenation (..) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand or object to concatenate. |
| `right` | `any` | Right operand or object to concatenate. |

**Returns:** `any`

## `__div`

Defines behavior for the division (/) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand of the division (dividend). |
| `right` | `any` | Right operand of the division (divisor). |

**Returns:** `any`

## `__eq`

Defines behavior for the equality (==) operator.

```lua
(left: {}, right: {}) -> boolean
```

| Name | Type | Description |
|---|---|---|
| `left` | `{}` | First value to compare. |
| `right` | `{}` | Second value to compare. |

**Returns:** `boolean`

## `__idiv`

Defines behavior for the floor division (//) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand of the floor division. |
| `right` | `any` | Right operand of the floor division. |

**Returns:** `any`

## `__index`

Called when looking up a key that does not exist in the table.

```lua
((self: {}, key: any) -> any) | { [any]: any }
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Table being accessed. |
| `key` | `any` | Key that was not found in the table. |

**Returns:** `any`

## `__iter`

Called before generalized iteration begins on a table or userdata. Returns an iterator generator function, a state object, and an initial control variable.

```lua
<S, K, V...>(self: {}) -> ((state: S, index: K) -> (K?, V...), S, K)
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Table or object being iterated. |

**Returns:** `((state: S, index: K) -> (K?, V...), S, K)`

## `__jsonhint`

String property used by lljson.encode to enforce table formatting rules.

```lua
"array" | "object"
```

## `__le`

Defines behavior for the less-than-or-equal-to (<=) operator.

```lua
(left: {}, right: {}) -> boolean
```

| Name | Type | Description |
|---|---|---|
| `left` | `{}` | Left operand of the comparison. |
| `right` | `{}` | Right operand of the comparison. |

**Returns:** `boolean`

## `__len`

Defines behavior for the length (#) operator.

```lua
(self: {}) -> number
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Object whose length is being measured. |

**Returns:** `number`

## `__lt`

Defines behavior for the less-than (<) operator.

```lua
(left: {}, right: {}) -> boolean
```

| Name | Type | Description |
|---|---|---|
| `left` | `{}` | Left operand of the comparison. |
| `right` | `{}` | Right operand of the comparison. |

**Returns:** `boolean`

## `__metatable`

Protects the metatable. If present, getmetatable returns this value, and setmetatable will raise an error.

```lua
any
```

## `__mod`

Defines behavior for the modulo (%) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand (dividend). |
| `right` | `any` | Right operand (divisor). |

**Returns:** `any`

## `__mode`

Controls weak mapping of table elements. Valid values are 'k' (weak keys), 'v' (weak values), or 'kv' (both).

```lua
"k" | "v" | "kv"
```

## `__mul`

Defines behavior for the multiplication (*) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand of the multiplication. |
| `right` | `any` | Right operand of the multiplication. |

**Returns:** `any`

## `__newindex`

Called when assigning a value to a key that does not exist in the table.

```lua
((self: {}, key: any, value: any) -> ()) | { [any]: any }
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Table being assigned. |
| `key` | `any` | Key being assigned. |
| `value` | `any` | Value being assigned to the key. |

**Returns:** `()`

## `__pow`

Defines behavior for the exponentiation (^) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Base value. |
| `right` | `any` | Exponent value. |

**Returns:** `any`

## `__sub`

Defines behavior for the subtraction (-) operator.

```lua
(left: any, right: any) -> any
```

| Name | Type | Description |
|---|---|---|
| `left` | `any` | Left operand of the subtraction (minuend). |
| `right` | `any` | Right operand of the subtraction (subtrahend). |

**Returns:** `any`

## `__tojson`

Called during JSON serialization (with lljson.encode or lljson.slencode). Returns an alternative representation of the table to be serialized in its place.

```lua
(self: {}, ctx: { mode: "json" | "sljson", tight: boolean }) -> any
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Table being serialized. |
| `ctx` | `{ mode: "json" | "sljson", tight: boolean }` | Context table containing metadata about the current serialization process, including 'mode' ('json' or 'sljson') and 'tight' (boolean). |

**Returns:** `any`

## `__tostring`

Called by tostring to convert the value to a string.

```lua
(self: {}) -> string
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Object being converted to a string. |

**Returns:** `string`

## `__unm`

Defines behavior for the unary negation (-) operator.

```lua
(self: {}) -> any
```

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | Value being negated. |

**Returns:** `any`
