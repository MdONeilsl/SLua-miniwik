# `ll.TeleportAgent`

```lua
ll.TeleportAgent(agent: uuid, landmark: string, position: vector, look_at: vector) -> ()
```

Moves the agent who owns the script (and must have granted PERMISSION_TELEPORT) to a specified landmark found in the object's inventory. If the landmark parameter is empty, the agent is teleported to the given position within the current region. After arrival, the agent is oriented to face the specified look_at vector. This function is restricted to teleporting the owner only.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the owning avatar to teleport. |
| `landmark` | `string` | Name of the landmark in the prim's inventory, or an empty string to teleport locally. |
| `position` | `vector` | Position vector in local region coordinates to teleport to if landmark is empty. |
| `look_at` | `vector` | Position vector (or direction unit vector if teleporting out of region) the agent faces upon landing. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `permissions`, `teleport` |
