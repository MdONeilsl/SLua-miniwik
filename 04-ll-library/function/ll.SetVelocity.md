# `ll.SetVelocity`

```lua
ll.SetVelocity(velocity: vector, is_local: boolean | number) -> ()
```

Assigns a specified linear velocity to a physical object, expressed in meters per second. When `is_local` is true, the velocity is interpreted as a direction relative to the object’s local coordinate system; when false, it is treated as a global region direction. This function has no effect on objects that are not physical.

## Arguments

| Name | Type | Description |
|---|---|---|
| `velocity` | `vector` | Linear velocity vector to apply (in meters per second). |
| `is_local` | `boolean | number` | Boolean. If TRUE, velocity is treated as a local directional vector; if FALSE, as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |