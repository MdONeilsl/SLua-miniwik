# `vector.lerp`

```lua
vector.lerp(start_vec: vector, end_vec: vector, t: number) -> vector
```

Computes a vector that lies along the straight line between start_vec and end_vec, scaled by the interpolation factor t.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start_vec` | `vector` | Initial point of the interpolation range. |
| `end_vec` | `vector` | Final point of the interpolation range. |
| `t` | `number` | Weight determining how far along the path to interpolate. |

**Returns:** `vector`