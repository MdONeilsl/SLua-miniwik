# `integer.mod`

```lua
integer.mod(dividend: integer, divisor: integer) -> integer
```

Calculates the signed remainder resulting from dividing the dividend by the divisor. The computed value's sign will always match the sign of the divisor; furthermore, it throws an error if the divisor is zero.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dividend` | `integer` | The integer number being divided. |
| `divisor` | `integer` | The integer value used as the divider. |

**Returns:** `integer`
