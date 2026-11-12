# `ll.SetForce`

```lua
ll.SetForce(force: vector, is_local: boolean | number) -> ()
```

Applies a steady linear force to a physical entity. When `is_local` is true, the force vector is interpreted in the object’s local coordinate system; otherwise, it is applied using the region’s global coordinate system.


## Arguments

| Name | Type | Description |
|---|---|---|
| `force` | `vector` | Directional force vector to apply. |
| `is_local` | `boolean | number` | Boolean. If TRUE, force is treated as a local vector; if FALSE, as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |
