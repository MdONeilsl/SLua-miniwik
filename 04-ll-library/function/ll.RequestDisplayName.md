# `ll.RequestDisplayName`

```lua
ll.RequestDisplayName(id: uuid) -> uuid
```

This function initiates an asynchronous request to obtain the display name of the agent identified by the given ID, which will trigger a dataserver event once the data is available. The targeted agent does not need to be connected or present in the current region. The function returns a key-based query handle.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar to query. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `dataserver` |
