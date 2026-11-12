# `select`

```lua
select(i: string | number, ...) -> ...any
```

This function retrieves a portion of arguments beginning at a specified position. It handles indexes counting backward from the end, and using '#' yields the total count of provided parameters.

## Arguments

| Name | Type | Description |
|---|---|---|
| `i` | `string | number` | The starting index, which can be an integer or '#' for the total argument count. |
| `...` | `A...` | The collection of arguments from which a subset will be chosen. |

**Returns:** `...any`
