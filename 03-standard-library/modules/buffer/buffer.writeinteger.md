# `buffer.writeinteger`

```lua
buffer.writeinteger(b: buffer, offset: number, value: integer) -> ()
```

Writes an integer that can be either signed or unsigned, utilizing 64 bits of storage within the provided buffer at a specified location.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer object for data storage. |
| `offset` | `number` | Starting byte position where the writing will occur. |
| `value` | `integer` | The integer value to be written into the memory block. |

**Returns:** `()`
