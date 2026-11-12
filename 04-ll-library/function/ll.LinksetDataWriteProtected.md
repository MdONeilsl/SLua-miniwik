# `ll.LinksetDataWriteProtected`

```lua
ll.LinksetDataWriteProtected(name: string, value: string, pass: string) -> number
```

Sets or modifies a protected key within the linkset datastore, using the specified passphrase, and emits a linkset_data event upon any change. Returns an integer indicating success or failure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | — |
| `value` | `string` | Value to write to the key (an empty string deletes the key). |
| `pass` | `string` | Passphrase used to protect or update the key. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |
