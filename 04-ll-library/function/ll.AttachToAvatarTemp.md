# `ll.AttachToAvatarTemp`

```lua
ll.AttachToAvatarTemp(attach_point: number) -> ()
```

Temporarily attaches the object to an avatar that has been granted the PERMISSION_ATTACH permission. This does not create a permanent inventory link, and the object vanishes when detached or when the avatar disconnects. It may be applied to non-owners, transferring ownership to the wearer.


## Arguments

| Name | Type | Description |
|---|---|---|
| `attach_point` | number | ATTACH_* constant or integer value representing the target attachment point. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `attachments`, `avatar` |