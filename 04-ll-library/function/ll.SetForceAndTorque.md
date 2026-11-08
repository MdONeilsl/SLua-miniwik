# `ll.SetForceAndTorque`

```lua
ll.SetForceAndTorque(force: vector, torque: vector, is_local: boolean | number) -> ()
```

Applies a constant linear force and a constant torque to a physical object. When `is_local` is true, the force and torque are interpreted in the object’s local coordinate system; when false, they are applied in the global region coordinate system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `force` | `vector` | Directional linear force vector. |
| `torque` | `vector` | Torque rotational force vector. |
| `is_local` | `boolean | number` | Boolean. If TRUE, force and torque are treated as local vectors; if FALSE, as global region vectors. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |