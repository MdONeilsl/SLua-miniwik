# `experience_permissions_denied`

```lua
experience_permissions_denied(agent_id: uuid, reason: number) -> ()
```

This event fires if an agent refuses access to experience, or if a block occurs for reasons detailed in the provided error number.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent_id` | `uuid` | The unique identifier for the user whose permissions were restricted. |
| `reason` | `number` | An enumeration value detailing the specific cause of the denial. |

**Returns:** `()`
