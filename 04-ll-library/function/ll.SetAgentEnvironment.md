# `ll.SetAgentEnvironment`

```lua
ll.SetAgentEnvironment(agent_id: uuid, transition: number, params: list) -> number
```

Applies environmental settings to a specific agent by specifying parameters in the params list, transitioning over the given duration in seconds. This function must be invoked within an experience context; supplying an empty list will clear any active overrides.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent_id` | `uuid` | UUID of the agent participating in the experience. |
| `transition` | `number` | Transition duration in seconds. |
| `params` | `list` | A list of environmental parameters to apply. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `experience`, `parcel_appearance`, `region_appearance` |