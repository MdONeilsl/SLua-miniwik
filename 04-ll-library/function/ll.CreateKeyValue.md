# `ll.CreateKeyValue`

```lua
ll.CreateKeyValue(k: string, v: string) -> uuid
```

Initiates an asynchronous operation to store a key-value pair (k, v) linked to the script's experience data. Provides a handle for subsequent dataserver event queries. If the key is already present, the operation fails with XP_ERROR_STORAGE_EXCEPTION.

## Arguments

| Name | Type | Description |
|---|---|---|
| `k` | `string` | Unique key name for the key-value pair. |
| `v` | `string` | Value for the key-value pair (maximum 2047 characters, or 4095 characters if using Mono). |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `experience`, `experience_data` |
