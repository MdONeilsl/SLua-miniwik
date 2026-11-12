# `math.fmod`

```lua
math.fmod(dividend: number, modulus: number) -> number
```

Computes the remainder when dividing the dividend by the modulus, with results rounded toward zero; returns NaN if the modulus is zero, and matches the behavior of the `%` operator when both operands share the same sign.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dividend` | `number` | The number to be divided. |
| `modulus` | `number` | The divisor used to compute the remainder. |

**Returns:** `number`
