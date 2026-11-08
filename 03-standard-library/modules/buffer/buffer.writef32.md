# `buffer.writef32`

```lua
buffer.writef32(b: buffer, offset: number, value: number) -> ()
```

This method writes a single 32-bit floating-point value into the provided buffer structure at the designated byte offset.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The buffer object receiving the data. |
| `offset` | `number` | The starting position in bytes, indexed from zero. |
| `value` | `number` | The floating-point number that should be stored. |

**Returns:** `()`