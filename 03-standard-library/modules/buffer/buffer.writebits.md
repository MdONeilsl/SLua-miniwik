# `buffer.writebits`

```lua
buffer.writebits(b: buffer, bitOffset: number, bitCount: number, value: number) -> ()
```

Writes a maximum of 32 bits into the specified location within the provided buffer object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The target buffer where data will be stored. |
| `bitOffset` | `number` | The starting position, measured in bits. |
| `bitCount` | `number` | How many bits are being written; must fall between 0 and 32. |
| `value` | `number` | The numerical value whose binary representation is written. |

**Returns:** `()`
