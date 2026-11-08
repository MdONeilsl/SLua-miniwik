# `quaternion.normalize`

```lua
quaternion.normalize(q: quaternion) -> quaternion
```

Computes a unit quaternion with the same rotational direction as the input, scaling it to unit length; returns identity if input is zero.

## Arguments

| Name | Type | Description |
|---|---|---|
| `q` | `quaternion` | Input quaternion to scale to unit magnitude. |

**Returns:** `quaternion`