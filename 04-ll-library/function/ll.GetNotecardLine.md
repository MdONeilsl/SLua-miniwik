# `ll.GetNotecardLine`

```lua
ll.GetNotecardLine(name: string | uuid, line: number) -> uuid
```

Initiates an asynchronous request to retrieve the specified line from the notecard, returning a query handle that will trigger a dataserver event; if the requested line exceeds the notecard’s content, the event will return EOF.


## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string | uuid` | Name of the notecard in the prim's inventory, or a UUID. |
| `line` | `number` | Index of the line to read. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `data_storage`, `dataserver`, `notecard` |