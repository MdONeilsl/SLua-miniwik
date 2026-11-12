# `ll.GetAgentInfo`

```lua
ll.GetAgentInfo(id: uuid) -> number
```

Returns an integer value representing a bitfield that encodes the current status of the agent identified by id, including flags like AGENT_FLYING, AGENT_ATTACHMENTS, and AGENT_SITTING.

## Arguments

| Name | Type | Description |
|---|---|---|
| id | uuid | UUID of the avatar in the same region. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |
