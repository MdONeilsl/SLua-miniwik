# `utf8.codepoint`

```lua
utf8.codepoint(src: string, start_index: number?, end_index: number?) -> ...number
```

Extracts the Unicode codepoint values for characters within the specified inclusive byte range in the string.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Input string to process. |
| `start_index` | `number?` | First byte position to include; defaults to 1. Accepts negative indices. |
| `end_index` | `number?` | Last byte position to include; defaults to string length. Accepts negative indices. |

**Returns:** `...number`
