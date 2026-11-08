# `buffer.writestring`

```lua
buffer.writestring(b: buffer, offset: number, value: string, count: number?) -> ()
```

Writes data from a specified string into the provided buffer starting at a given position. This operation transfers part of the string content to the designated location within the memory buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer object receiving the written data. |
| `offset` | `number` | Starting position in bytes, counted from zero. |
| `value` | `string` | The string content that needs to be outputted. |
| `count` | `number?` | Optional limit specifying how many bytes are transferred. |

**Returns:** `()`