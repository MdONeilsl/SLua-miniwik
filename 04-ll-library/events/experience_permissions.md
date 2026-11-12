# `experience_permissions`

```lua
experience_permissions(agent_id: uuid) -> ()
```

This event executes whenever the designated user grants permission for an experience, regardless of whether that approval was manual or pre-set.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent_id` | `uuid` | The unique identifier for the user granting access rights. |

**Returns:** `()`
