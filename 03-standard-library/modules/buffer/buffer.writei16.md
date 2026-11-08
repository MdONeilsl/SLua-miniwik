# `buffer.writei16`

```lua
buffer.writei16(b: buffer, offset: number, value: number) -> ()
```

This function stores a signed number that occupies 16 bits into the specified location within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer object for writing data. |
| `offset` | `number` | Specifies the starting position in bytes, zero-indexed. |
| `value` | `number` | The numerical value that will be stored. |

**Returns:** `()`