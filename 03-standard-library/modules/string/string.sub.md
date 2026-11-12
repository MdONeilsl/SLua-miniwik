# `string.sub`

```lua
string.sub(src: string, start_index: number, end_index: number?) -> string
```

Extracts a contiguous segment of bytes from the source string, bounded inclusively by the specified start and end positions, with support for negative indices to count from the end.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | The string to extract a portion from, with backward indexing allowed. |
| `start_index` | `number` | The first byte position to include, counted from the start or end. |
| `end_index` | `number?` | The last byte position to include, or the string’s end if not provided; also supports reverse counting. |

**Returns:** `string`
