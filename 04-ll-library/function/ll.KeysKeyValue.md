# `ll.KeysKeyValue`

```lua
ll.KeysKeyValue(first: number, count: number) -> uuid
```

Initiates an asynchronous operation to fetch a specified number of keys from the experience data store, beginning at the given zero-based index. The function yields a handle used for the dataserver event; if the requested keys are beyond the available range, it returns XP_ERROR_KEY_NOT_FOUND.


## Arguments

| Name | Type | Description |
|---|---|---|
| `first` | `number` | Zero-based start index of the keys to retrieve. |
| `count` | `number` | Number of keys to retrieve. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `experience`, `experience_data` |