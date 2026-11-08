# `integer.rem`

```lua
integer.rem(dividend: integer, divisor: integer) -> integer
```

Calculates the signed remainder obtained when dividing the dividend by the divisor. The sign of this result will always match the sign of the original dividend; furthermore, executing this function fails if the divisor is zero.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dividend` | `integer` | The integer value being divided. |
| `divisor` | `integer` | The integer used to perform the division. |

**Returns:** `integer`