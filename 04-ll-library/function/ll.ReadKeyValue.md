# `ll.ReadKeyValue`

```lua
ll.ReadKeyValue(k: string) -> uuid
```

Initiates an asynchronous operation to retrieve the value linked to key k within the experience context. Provides a handle for the dataserver event, which can be used to track the result. If the specified key is not present, the operation will fail with the error code XP_ERROR_KEY_NOT_FOUND.


## Arguments

| Name | Type | Description |
|---|---|---|
| `k` | `string` | Key of the key-value pair to read. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `experience`, `experience_data` |