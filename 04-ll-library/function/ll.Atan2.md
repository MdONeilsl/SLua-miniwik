# `ll.Atan2`

```lua
ll.Atan2(y: number, x: number) -> number
```

Computes the arctangent of the ratio y/x, expressed in radians, while preserving quadrant information through the sign of the inputs. The function accepts y as the first argument and x as the second, in that order.


## Arguments

| Name | Type | Description |
|---|---|---|
| `y` | number | Y coordinate. |
| `x` | number | X coordinate. |

**Returns:** `number`

## Deprecated

- **use:** math.atan2
- **reason:** Double precision; fastcall.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_trig` |