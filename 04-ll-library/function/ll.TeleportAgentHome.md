# `ll.TeleportAgentHome`

```lua
ll.TeleportAgentHome(avatar: uuid) -> ()
```

Instantly transports the specified avatar to their assigned home position, bypassing any warning or confirmation, akin to a God Summons. The avatar must be positioned on land that belongs to the script's owner for this action to succeed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar to teleport. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `100.0` |
| `sleep` | `5.0` |
| `categories` | `avatar`, `land_moderation`, `teleport` |