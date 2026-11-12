# `ll.LinksetDataWrite`

```lua
ll.LinksetDataWrite(name: string, value: string) -> number
```

Sets or modifies an unprotected key in the linkset datastore with the specified value, which will also trigger a linkset_data event if the datastore is modified. The function returns an integer indicating success or failure.


## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | — |
| `value` | `string` | Value to write to the key (an empty string deletes the key). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |
