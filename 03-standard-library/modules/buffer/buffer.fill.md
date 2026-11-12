# `buffer.fill`

```lua
buffer.fill(b: buffer, offset: number, value: number, count: number?) -> ()
```

This method writes a specific numeric value to a designated portion of a buffer. The writing process commences at an initial byte position within the target object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The buffer object that will receive the data. |
| `offset` | `number` | Starting position in bytes (zero indexed). |
| `value` | `number` | The numeric value used for filling the buffer. |
| `count` | `number?` | Optional count specifying how many bytes are written. |

**Returns:** `()`
