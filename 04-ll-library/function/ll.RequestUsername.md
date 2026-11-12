# `ll.RequestUsername`

```lua
ll.RequestUsername(id: uuid) -> uuid
```

Initiates an asynchronous lookup for the unique, single-word username associated with the specified agent ID, which triggers a dataserver event. The target agent does not need to be currently online or present in the region. The function returns a key representing the query handle.


## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | uuid | UUID of the avatar to query. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `dataserver` |
