# `ll.DeleteKeyValue`

```lua
ll.DeleteKeyValue(k: string) -> uuid
```

Initiates an asynchronous operation to remove the key-value entry linked to key k from the experience. Provides a handle for the dataserver event.

## Arguments

| Name | Type | Description |
|---|---|---|
| `k` | `string` | Key of the key-value pair to delete. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `experience`, `experience_data` |
