# `buffer.readu32`

```lua
buffer.readu32(b: buffer, offset: number) -> number
```

This function retrieves a value of 32 bits, treated as unsigned, using the specified position within the provided data structure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The source buffer containing the bytes to read. |
| `offset` | `number` | Starting byte index for reading, counted from zero. |

**Returns:** `number`