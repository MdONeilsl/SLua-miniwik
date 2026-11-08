# `ll.ReleaseCamera`

```lua
ll.ReleaseCamera(avatar: uuid) -> ()
```

This function is obsolete and was designed to restore camera control to the avatar; replace it with ll.ClearCameraParams.


## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar in the same region. |

**Returns:** `()`

## Deprecated

- **use:** ll.ClearCameraParams

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `camera`, `permissions` |