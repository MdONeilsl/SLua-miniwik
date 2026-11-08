# `buffer.readinteger`

```lua
buffer.readinteger(b: buffer, offset: number) -> integer
```

Retrieves either a signed or unsigned whole number of 64 bits stored in the buffer starting at the specified position.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The data container from which to read the value. |
| `offset` | `number` | Starting byte index within the buffer for reading. |

**Returns:** `integer`