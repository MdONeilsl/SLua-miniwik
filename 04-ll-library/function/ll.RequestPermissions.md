# `ll.RequestPermissions`

```lua
ll.RequestPermissions(agent: uuid, permissions: number) -> ()
```

Initiates a request for specified permissions (as a bitfield) from an agent located in the same region; if granted, triggers the run_time_permissions function. Execution of the script continues without interruption.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the agent in the same region. |
| `permissions` | `number` | Bitfield containing the PERMISSION_* constants to request. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `permissions` |
