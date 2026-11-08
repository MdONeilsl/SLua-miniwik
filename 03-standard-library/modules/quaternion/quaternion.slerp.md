# `quaternion.slerp`

```lua
quaternion.slerp(start_q: quaternion, end_q: quaternion, t: number) -> quaternion
```

Computes a smoothly interpolated quaternion between start_q and end_q, weighted by t, following a spherical path.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start_q` | `quaternion` | Initial orientation for interpolation. |
| `end_q` | `quaternion` | Target orientation for interpolation. |
| `t` | `number` | Blend ratio from start to end, 0 to 1. |

**Returns:** `quaternion`