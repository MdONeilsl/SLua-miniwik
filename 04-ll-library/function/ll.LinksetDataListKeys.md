# `ll.LinksetDataListKeys`

```lua
ll.LinksetDataListKeys(start: number, count: number) -> {string}
```

This function retrieves a sorted list of keys from the linkset datastore, beginning at the specified index and limited by the count parameter; if count is less than 1, it returns all available keys.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start` | number | Index of the first key to return. |
| `count` | number | Maximum number of keys to return (or less than 1 to retrieve all keys). |

**Returns:** `{string}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |