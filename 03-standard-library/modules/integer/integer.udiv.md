# `integer.udiv`

```lua
integer.udiv(dividend: integer, divisor: integer) -> integer
```

Calculates the unsigned quotient of dividend divided by divisor. The result is rounded down towards negative infinity; running this function with a zero divisor will trigger an error.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dividend` | `integer` | The whole number value being divided. |
| `divisor` | `integer` | The integer used to perform the division operation. |

**Returns:** `integer`
