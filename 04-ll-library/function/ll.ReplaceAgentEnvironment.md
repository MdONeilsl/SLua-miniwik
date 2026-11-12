# `ll.ReplaceAgentEnvironment`

```lua
ll.ReplaceAgentEnvironment(agent_id: uuid, transition: number, environment: string | uuid) -> number
```

Sets the environment visible to the specified agent during an experience, smoothly transitioning over the given time in seconds. Using NULL_KEY or an empty string reverts to default settings.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent_id` | `uuid` | UUID of an agent in the region participating in the experience. |
| `transition` | `number` | Duration in seconds over which to transition to the new environment. |
| `environment` | `string | uuid` | Name of an environmental setting in inventory, or its asset UUID (or empty string/NULL_KEY to clear). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `experience`, `parcel_appearance`, `region_appearance` |
