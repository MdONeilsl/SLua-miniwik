# `ll.SetTorque`

```lua
ll.SetTorque(torque: vector, is_local: boolean | number) -> ()
```

Applies a continuous rotational force as torque to a physical object. When `is_local` is true, the torque is interpreted in the object’s local coordinate system; when false, it is applied in the global coordinate system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `torque` | `vector` | Torque rotational force vector. |
| `is_local` | `boolean | number` | Boolean. If TRUE, torque is treated as a local vector; if FALSE, as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |