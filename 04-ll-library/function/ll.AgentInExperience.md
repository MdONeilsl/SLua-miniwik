# `ll.AgentInExperience`

```lua
ll.AgentInExperience(agent: uuid) -> boolean
```

Returns true if the given agent is present in the experience and the experience is permitted to execute within the current region; returns false if either condition is not met.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the avatar in the same region to query. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `experience` |