# `ll.AxisAngle2Rot`

```lua
ll.AxisAngle2Rot(axis: vector, angle: number) -> quaternion
```

Given an axis vector and an angle in radians, this function computes and returns the corresponding rotation that performs a rotation about that axis by the specified angle.


## Arguments

| Name | Type | Description |
|---|---|---|
| `axis` | `vector` | Axis vector to rotate around. |
| `angle` | `number` | Angle to rotate, in radians. |

**Returns:** `quaternion`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `math_trig`, `quaternion` |
