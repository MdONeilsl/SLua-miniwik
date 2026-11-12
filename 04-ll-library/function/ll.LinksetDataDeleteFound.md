# `ll.LinksetDataDeleteFound`

```lua
ll.LinksetDataDeleteFound(pattern: string, pass: string) -> {number}
```

Removes all keys from the linkset datastore that conform to the given regular expression, emitting a linkset_data event if the datastore is modified. Protected keys are removed only when their passphrase matches the provided pass. The function returns a list containing [number of keys deleted, number of protected keys that failed to delete].

## Arguments

| Name | Type | Description |
|---|---|---|
| pattern | `string` | Regular expression (regex) matching the keys to delete. |
| pass | `string` | Optional passphrase required to delete matching protected keys. |

**Returns:** `{number}`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `data_storage`, `linkset`, `linkset_data` |
