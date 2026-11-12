# `buffer.copy`

```lua
buffer.copy(target: buffer, targetOffset: number, source: buffer, sourceOffset: number?, count: number?) -> ()
```

This function transfers a specified quantity of bytes from one buffer (the source) to another (the target). The data is copied starting at defined offsets within both buffers.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `buffer` | The destination buffer where the bytes will be written. |
| `targetOffset` | `number` | Starting byte index within the destination buffer. |
| `source` | `buffer` | The buffer containing the data that needs copying. |
| `sourceOffset` | `number?` | Starting byte index within the origin buffer. |
| `count` | `number?` | The total amount of bytes that should be copied. |

**Returns:** `()`
