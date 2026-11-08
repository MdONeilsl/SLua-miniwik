# `ll.RotLookAt`

```lua
ll.RotLookAt(target_direction: quaternion, strength: number, damping: number) -> ()
```

Initiates a gradual rotation of the object toward the specified target_direction, modulated by the strength and damping parameters. Setting strength to 0.0 disables the rotation target. The rotation persists until explicitly halted by ll.StopLookAt.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target_direction` | `quaternion` | Target rotation to align the object with. |
| `strength` | `number` | Force of rotation (0.0 cancels the tracking; values around half the object's mass are typical). |
| `damping` | `number` | Timescale in seconds to critically damp the rotation. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |