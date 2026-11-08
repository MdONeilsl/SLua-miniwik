# `integer.rshift`

```lua
integer.rshift(val: integer, i: integer) -> integer
```

Shifts the integer `val` right by `i` bits; negative `i` reverses direction. Result is zero if `i` is outside [-63, 63].

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `integer` | Value to be bitwise shifted. |
| `i` | `integer` | Bit displacement amount, signed. |

**Returns:** `integer`
