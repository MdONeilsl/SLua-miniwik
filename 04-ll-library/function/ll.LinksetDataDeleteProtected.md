# `ll.LinksetDataDeleteProtected`

```lua
ll.LinksetDataDeleteProtected(name: string, pass: string) -> number
```

Removes the specified protected key from the linkset datastore by using the provided passphrase, which may cause a linkset_data event if the datastore is modified. The function returns an integer indicating whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | — |
| `pass` | `string` | Passphrase required to delete the protected key. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |
