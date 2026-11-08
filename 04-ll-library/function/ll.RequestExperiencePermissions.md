# `ll.RequestExperiencePermissions`

```lua
ll.RequestExperiencePermissions(agent: uuid, name: string) -> ()
```

This function prompts the designated agent for permission to join the experience. The granted permissions are persistent and affect all scripts within the experience across the entire grid, which will automatically invoke either experience_permissions or experience_permissions_denied.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the agent to request permissions from. |
| `name` | `string` | |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `experience`, `permissions` |