# `table.concat`

```lua
table.concat(a: {string | number}, sep: string?, i: number?, j: number?) -> string
```

Joins elements of an array into a single string, using a specified separator between items; optional start and end indices define the range to process.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{string | number}` | Collection of values to join. |
| `sep` | `string?` | String inserted between each element. |
| `i` | `number?` | First index to include in the join. |
| `j` | `number?` | Last index to include in the join. |

**Returns:** `string`
