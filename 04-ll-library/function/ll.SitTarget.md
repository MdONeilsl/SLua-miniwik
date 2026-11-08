# `ll.SitTarget`

```lua
ll.SitTarget(offset: vector, rot: quaternion) -> ()
```

Defines the target position and orientation for sitting, relative to the prim’s local coordinates; if the offset is set to ZERO_VECTOR, the sit target is cleared.


## Arguments

| Name | Type | Description |
|---|---|---|
| `offset` | `vector` | Target position vector in local prim coordinates. |
| `rot` | `quaternion` | Target rotation relative to the prim's rotation. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim`, `sit` |