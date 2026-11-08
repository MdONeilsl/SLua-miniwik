# `buffer.writei8`

```lua
buffer.writei8(b: buffer, offset: number, value: number) -> ()
```

This method stores an 8-bit value, treating it as a signed integer, into the specified location within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer object for writing data. |
| `offset` | `number` | Starting position, measured in bytes from zero. |
| `value` | `number` | The numerical value that should be stored. |

**Returns:** `()`