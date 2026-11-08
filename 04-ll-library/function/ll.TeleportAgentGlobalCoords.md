# `ll.TeleportAgentGlobalCoords`

```lua
ll.TeleportAgentGlobalCoords(agent: uuid, global_coordinates: vector, region_coordinates: vector, look_at: vector) -> ()
```

Moves the agent who owns the script (and must have granted PERMISSION_TELEPORT) to a specified location within a region defined by global_coordinates. Upon arrival, the agent orients itself toward the look_at vector. This function is restricted to teleporting the script’s owner only.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the owning avatar to teleport. |
| `global_coordinates` | `vector` | Global coordinates vector of the target region (obtained via ll.RequestSimulatorData). |
| `region_coordinates` | `vector` | Target coordinates vector within the destination region. |
| `look_at` | `vector` | Position vector within the region (or unit direction vector if out of region) that the agent faces upon landing. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `permissions`, `teleport` |