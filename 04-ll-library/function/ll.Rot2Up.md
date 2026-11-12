# `ll.Rot2Up`

```lua
ll.Rot2Up(q: quaternion) -> vector
```

Given a quaternion q, this function computes the unit vector aligned with the positive Z-axis in the coordinate system defined by q, which is mathematically equivalent to applying q to the vector <0, 0, 1>.

## Arguments

| Name | Type | Description |
|---|---|---|
| q | quaternion | Rotation to convert. |

**Returns:** `vector`

## Deprecated

- **use:** quaternion.toup

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | math, math_3d, math_trig, quaternion, vector |
