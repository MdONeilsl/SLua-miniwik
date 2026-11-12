# `dataserver`

```lua
dataserver(queryid: uuid, data: string) -> ()
```

The script receives this signal once asynchronous data retrieval is complete, such as results from `ll.RequestInventoryData`, `ll.RequestAgentData`, or `ll.GetNotecardLine`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `queryid` | `uuid` | Unique ID matching the handle from the originating function call. |
| `data` | `string` | The actual string content that was originally requested. |

**Returns:** `()`
