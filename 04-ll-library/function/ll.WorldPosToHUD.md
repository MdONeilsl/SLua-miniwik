# `ll.WorldPosToHUD`

```lua
ll.WorldPosToHUD(world_pos: vector) -> vector
```

Converts a world-space position into a HUD-space vector, positioning the center of a HUD element directly over that world coordinate from the perspective of the current camera. This function requires the PERMISSION_TRACK_CAMERA runtime permission to operate.

## Arguments

| Name | Type | Description |
|---|---|---|
| `world_pos` | `vector` | World-frame position vector to project into HUD space. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `camera`, `permissions`, `user_interface` |