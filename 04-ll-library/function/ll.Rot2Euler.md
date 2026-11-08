# `ll.Rot2Euler`

```lua
ll.Rot2Euler(quat: quaternion) -> vector
```

Given a quaternion `q`, this function computes and returns the corresponding Euler angles—specifically roll, pitch, and yaw—in radians, packaged as a vector.


## Arguments

| Name | Type | Description |
|---|---|---|
| quat | `quaternion` | Rotation to convert. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `math`, `math_3d`, `quaternion` |