# `buffer.readbits`

```lua
buffer.readbits(b: buffer, bitOffset: number, bitCount: number) -> number
```

The function retrieves a sequence of bits, limited to a maximum of 32, starting from a specific position within the buffer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The source buffer data structure. |
| `bitOffset` | `number` | The starting bit position within the buffer. |
| `bitCount` | `number` | Specifies the quantity of bits; must fall between 0 and 32. |

**Returns:** `number`