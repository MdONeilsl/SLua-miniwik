# `quaternion.tofwd`

```lua
quaternion.tofwd(q: quaternion) -> vector
```

The function extracts the forward direction vector in the coordinate frame defined by the input quaternion, equivalent to rotating the standard X-axis by that rotation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `q` | `quaternion` | Rotation quaternion to apply to the forward axis. |

**Returns:** `vector`
