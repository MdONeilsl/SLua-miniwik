# `ll.Rot2Fwd`

```lua
ll.Rot2Fwd(q: quaternion) -> vector
```

Given a quaternion q, this function computes the unit vector that aligns with the positive X-axis in the local coordinate system defined by q, which is mathematically equivalent to applying the rotation q to the vector <1, 0, 0>.

## Arguments

| Name | Type | Description |
|---|---|---|
| q | quaternion | Rotation to convert. |

**Returns:** `vector`

## Deprecated

- **use:** quaternion.tofwd
- **reason:** Use quaternion.tofwd instead.

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `math`, `math_3d`, `math_trig`, `quaternion`, `vector` |