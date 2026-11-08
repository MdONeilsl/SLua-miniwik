# `bit32.lrotate`

```lua
bit32.lrotate(val: number, i: number) -> number
```

Rotates the given value by a specified count of bits to the left. Should the rotation amount be negative, this operation performs an equivalent right rotation instead.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The numerical value that will undergo bit rotation. |
| `i` | `number` | The count specifying the magnitude of the bit shift. |

**Returns:** `number`