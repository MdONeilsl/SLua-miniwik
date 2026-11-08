# `ll.GetCameraRot`

```lua
ll.GetCameraRot() -> quaternion
```

Returns the current rotational orientation of the camera as a rotation value, provided the agent has granted PERMISSION_TRACK_CAMERA. If the required permission is not held, the function returns ZERO_ROTATION.


## Arguments

_No arguments._

**Returns:** `quaternion`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `camera`, `permissions` |