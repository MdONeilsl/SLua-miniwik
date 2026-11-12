# `ll.Rot2Left`

```lua
ll.Rot2Left(q: quaternion) -> vector
```

Given a quaternion q, this function computes the unit vector aligned with the positive Y-axis in the local coordinate system defined by q, which is mathematically equivalent to applying the rotation q to the vector <0, 1, 0>.

## Arguments

| Name | Type | Description |
|---|---|---|
| `q` | `quaternion` | Rotation to convert. |

**Returns:** `vector`

## Deprecated

- **use:** quaternion.toleft

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `math_trig`, `quaternion`, `vector` |
