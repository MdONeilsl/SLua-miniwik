# `bit32.rshift`

```lua
bit32.rshift(val: number, i: number) -> number
```

Shifts the integer `val` right by `i` bits; if `i` is negative, shifts left instead. Result is zero if `i` is outside [-31, 31].

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | Value to be bit-shifted as an integer. |
| `i` | `number` | Bit displacement count, positive for right, negative for left. |

**Returns:** `number`
