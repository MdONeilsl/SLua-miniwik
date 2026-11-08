# `ll.TransferOwnership`

```lua
ll.TransferOwnership(agent: uuid, flags: number, options: list) -> number
```

Assigns ownership of the object—or a replica if specified by the Flags—to the designated agent, and returns an integer value reflecting whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the agent to receive ownership of the object. |
| `flags` | `number` | Flags controlling the transfer type (such as TRANSFER_FLAG_COPY or TRANSFER_FLAG_TAKE). |
| `options` | `list` | Extra options applied to the transfer (currently unused). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `asset_permissions` |