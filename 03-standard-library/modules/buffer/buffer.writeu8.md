# `buffer.writeu8`

```lua
buffer.writeu8(b: buffer, offset: number, value: number) -> ()
```

Writes a single unsigned byte value into the specified location within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The buffer object receiving the data. |
| `offset` | `number` | The specific starting byte index for writing. |
| `value` | `number` | The numerical value that should be stored. |

**Returns:** `()`