# `ll.SitOnLink`

```lua
ll.SitOnLink(agent_id: uuid, link: number) -> number
```

Causes the avatar identified by agent_id—requiring active participation in the experience—to occupy a sit target on the prim referenced by link. If the target is already occupied, the function traverses the linkset downward to locate an unoccupied sit target. The function yields an integer result.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent_id` | `uuid` | UUID of the avatar being forced to sit. |
| `link` | `number` | Link number for the prim containing the desired sit target. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `experience`, `sit` |
