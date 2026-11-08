# `integer.arshift`

```lua
integer.arshift(val: integer, i: integer) -> integer
```

Computes an arithmetic right shift of val by i bits; if i is negative, the operation performs a left shift instead. This process ensures that the most significant bit remains constant throughout the shifting action.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `integer` | The integer value that will be shifted. |
| `i` | `integer` | The amount, in bits, by which to shift the value. |

**Returns:** `integer`