# `buffer.writei32`

```lua
buffer.writei32(b: buffer, offset: number, value: number) -> ()
```

This method stores a signed integer using 32 bits into the specified location within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer object for writing data. |
| `offset` | `number` | The starting position in bytes, indexed from zero. |
| `value` | `number` | The numerical value that needs to be stored. |

**Returns:** `()`