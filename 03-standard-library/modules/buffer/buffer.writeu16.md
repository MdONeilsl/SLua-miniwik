# `buffer.writeu16`

```lua
buffer.writeu16(b: buffer, offset: number, value: number) -> ()
```

Stores an unsigned whole number occupying sixteen bits within the specified buffer position.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The destination buffer where data will be stored. |
| `offset` | `number` | The starting location within the buffer, measured in zero-indexed bytes. |
| `value` | `number` | The numeric quantity that needs to be saved into the buffer. |

**Returns:** `()`