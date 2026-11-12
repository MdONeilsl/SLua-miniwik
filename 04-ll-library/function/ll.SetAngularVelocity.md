# `ll.SetAngularVelocity`

```lua
ll.SetAngularVelocity(initial_omega: vector, is_local: boolean | number) -> ()
```

Applies an angular velocity vector, initial_omega, to a physical object regardless of its mass. When is_local is true, the vector is interpreted in the object’s local coordinate system; when false, it is applied in the global coordinate system. This function does not affect non-physical objects.

## Arguments

| Name | Type | Description |
|---|---|---|
| initial_omega | `vector` | Angular velocity vector to apply (in radians per second). |
| is_local | `boolean | number` | Boolean. If TRUE, initial_omega is treated as a local vector; if FALSE, as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `movement`, `physics` |
