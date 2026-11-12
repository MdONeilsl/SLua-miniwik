# `ll.LinksetDataDelete`

```lua
ll.LinksetDataDelete(name: string) -> number
```

Removes the specified unprotected key from the linkset datastore, which may trigger a linkset_data event if the datastore is modified. The function returns an integer indicating success or failure.


## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | string | — |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |
