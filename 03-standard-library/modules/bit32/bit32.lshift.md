# `bit32.lshift`

```lua
bit32.lshift(val: number, i: number) -> number
```

Shifts the integer `val` left by `i` bits; negative `i` causes a right shift. Result is zero if `i` is outside [-31, 31].

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | Value to be bit-shifted as an integer. |
| `i` | `number` | Bit displacement count; positive for left, negative for right. |

**Returns:** `number`
