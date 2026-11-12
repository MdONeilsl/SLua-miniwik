# `ll.Axes2Rot`

```lua
ll.Axes2Rot(fwd: vector, left: vector, up: vector) -> quaternion
```

Constructs a rotation from the given forward, left, and up vectors that define a local coordinate system.


## Arguments

| Name | Type | Description |
|---|---|---|
| `fwd` | `vector` | Forward/back directional vector of the rotation. |
| `left` | `vector` | Left/right directional vector of the rotation. |
| `up` | `vector` | Up/down directional vector of the rotation. |

**Returns:** `quaternion`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `math_trig`, `quaternion` |
