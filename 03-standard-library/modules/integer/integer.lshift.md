# `integer.lshift`

```lua
integer.lshift(val: integer, i: integer) -> integer
```

Shifts the given integer left by `i` bits; negative `i` reverses direction. Result is zero if shift exceeds [-63, 63].

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `integer` | Value to be bitwise shifted. |
| `i` | `integer` | Bit displacement count, positive or negative. |

**Returns:** `integer`
