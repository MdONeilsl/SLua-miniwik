# `math.clamp`

```lua
math.clamp(val: number, min: number, max: number) -> number
```

Constrains `val` to lie within the range defined by `min` and `max`, returning the closest valid value; throws an error if `min` exceeds `max`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | Value to restrict within bounds. |
| `min` | `number` | Lower boundary for the clamped result. |
| `max` | `number` | Upper boundary for the clamped result. |

**Returns:** `number`
