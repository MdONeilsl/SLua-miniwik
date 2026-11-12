# `buffer.writef64`

```lua
buffer.writef64(b: buffer, offset: number, value: number) -> ()
```

This function saves a double-precision floating point number into the specified location within the provided buffer object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer where data will be written. |
| `offset` | `number` | Starting byte position, counted from zero. |
| `value` | `number` | The numeric value to be stored in the buffer. |

**Returns:** `()`
