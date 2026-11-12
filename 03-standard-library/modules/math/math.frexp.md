# `math.frexp`

```lua
math.frexp(val: number) -> (number, number)
```

This function decomposes a given floating-point number into its significand component and an associated integer exponent. It returns the pair (s, e) such that the original value equals s multiplied by 2 raised to the power of e.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The input number for decomposition. |

**Returns:** `(number, number)`
