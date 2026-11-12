# `buffer.writeu32`

```lua
buffer.writeu32(b: buffer, offset: number, value: number) -> ()
```

This method stores a 32-bit unsigned whole number into the specified location within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The destination buffer object. |
| `offset` | `number` | The starting position in bytes (zero indexed). |
| `value` | `number` | The numerical value being stored. |

**Returns:** `()`
