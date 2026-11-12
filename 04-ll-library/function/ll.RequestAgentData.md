# `ll.RequestAgentData`

```lua
ll.RequestAgentData(id: uuid, data: number) -> uuid
```

Initiates an asynchronous request for a specific data category (DATA_*) associated with the given agent ID. Sends a dataserver event upon completion and returns a key representing the query handle.


## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the agent. |
| `data` | `number` | DATA_* category flag of the requested information. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `avatar`, `dataserver` |
