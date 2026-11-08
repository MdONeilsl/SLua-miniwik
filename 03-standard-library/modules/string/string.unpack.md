# `string.unpack`

```lua
string.unpack(format_string: string, src: string, start: number?) -> ...any
```

Decodes binary data from `src` using `format_string`, beginning at `start`, and yields the parsed values along with the next unread byte position.

## Arguments

| Name | Type | Description |
|---|---|---|
| `format_string` | `string` | Specifies the binary layout to interpret the data. |
| `src` | `string` | The binary data to decode. |
| `start` | `number?` | Initial byte position to begin parsing; defaults to 1. Accepts negative indices. |

**Returns:** `...any`