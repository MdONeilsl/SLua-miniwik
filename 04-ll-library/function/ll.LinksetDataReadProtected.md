# `ll.LinksetDataReadProtected`

```lua
ll.LinksetDataReadProtected(name: string, pass: string) -> string
```

Retrieves the value associated with the specified protected key in the linkset datastore, using the provided passphrase. If the key is not present or the passphrase is incorrect, an empty string is returned.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | Name of the protected key to read. |
| `pass` | `string` | Passphrase required to read the protected key. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |