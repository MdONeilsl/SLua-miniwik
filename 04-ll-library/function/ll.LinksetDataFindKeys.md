# `ll.LinksetDataFindKeys`

```lua
ll.LinksetDataFindKeys(pattern: string, start: number, count: number) -> {string}
```

Returns a sorted list of keys from the linkset datastore, in alphabetical order, that match the given regex pattern. The list includes up to count keys, beginning from the index specified by start; if count is less than 1, all matching keys are returned.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pattern` | `string` | Regular expression (regex) matching the keys to return. |
| `start` | `number` | Index of the first matching key to return. |
| `count` | `number` | Maximum number of keys to return (or less than 1 to retrieve all matching keys). |

**Returns:** `{string}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `linkset`, `linkset_data` |