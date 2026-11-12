# `ll.TakeCamera`

```lua
ll.TakeCamera(avatar: uuid) -> ()
```

This function is now deprecated; use ll.SetCameraParams instead. It was previously used to assume control of the agent’s camera.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar in the same region. |

**Returns:** `()`

## Deprecated

- **use:** ll.SetCameraParams

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `camera`, `permissions` |
