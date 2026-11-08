# `ll.ApplyRotationalImpulse`

```lua
ll.ApplyRotationalImpulse(force: vector, is_local: boolean | number) -> ()
```

This function imparts a rotational force onto a physical entity. When `is_local` is set to TRUE, the force vector is interpreted in the object’s local coordinate system; when FALSE, it is applied using the global region coordinate system.


## Arguments

| Name | Type | Description |
|---|---|---|
| `force` | `vector` | Rotational impulse vector to apply. |
| `is_local` | `boolean | number` | Boolean. If TRUE, the force is treated as a local directional vector; if FALSE, it is treated as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |