# `math.lerp`

```lua
math.lerp(start_val: number, end_val: number, t: number) -> number
```

Computes a weighted blend between start_val and end_val, where t controls the proportion of the transition from start to end.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start_val` | `number` | Value at the beginning of the interpolation range. |
| `end_val` | `number` | Value at the end of the interpolation range. |
| `t` | `number` | Weight between 0 and 1 determining how far along the interpolation path. |

**Returns:** `number`