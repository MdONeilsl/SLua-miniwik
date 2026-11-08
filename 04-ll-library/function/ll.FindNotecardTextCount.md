# `ll.FindNotecardTextCount`

```lua
ll.FindNotecardTextCount(notecardname: string | uuid, pattern: string, options: list) -> uuid
```

Initiates an asynchronous search to count occurrences of the specified pattern within the notecard's name, returning a query handle that can be used to retrieve the result from the dataserver event.


## Arguments

| Name | Type | Description |
|---|---|---|
| `notecardname` | `string | uuid` | Name of the notecard in the prim's inventory, or a UUID. |
| `pattern` | `string` | Regular expression pattern to search for. |
| `options` | `list` | A list of options to control the search (currently unused, should be []). |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `notecard` |