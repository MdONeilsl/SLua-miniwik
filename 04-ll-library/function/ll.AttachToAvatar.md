# `ll.AttachToAvatar`

```lua
ll.AttachToAvatar(attach_point: number) -> ()
```

When called, this function binds the object to the avatar possessing the PERMISSION_ATTACH permission, places the object into the user’s inventory, and secures it at the specified attach_point.


## Arguments

| Name | Type | Description |
|---|---|---|
| `attach_point` | `number` | ATTACH_* constant or integer value representing the target attachment point. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `attachments`, `avatar` |
