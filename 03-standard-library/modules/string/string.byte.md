# `string.byte`

```lua
string.byte(src: string, start_index: number?, end_index: number?) -> ...number
```

Extracts the numeric byte values from the specified range within the string, inclusive of both endpoints, using zero-based indexing with support for negative positions.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Input string to extract byte codes from. |
| `start_index` | `number?` | First byte position to include, defaulting to 1; negative values count from the end. |
| `end_index` | `number?` | Last byte position to include, defaulting to the string’s length; negative values count from the end. |

**Returns:** `...number`