# `math.ldexp`

```lua
math.ldexp(significand: number, exponent: number) -> number
```

Computes the product of the significand scaled by 2 raised to the exponent, reversing the decomposition done by `math.frexp`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `significand` | `number` | Base value to scale by a power of two. |
| `exponent` | `number` | Power of two to multiply the significand by. |

**Returns:** `number`
