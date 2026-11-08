# `ll.RemoteDataReply`

```lua
ll.RemoteDataReply(channel: uuid, message_id: uuid, sdata: string, idata: number) -> ()
```

This function is obsolete and used to send an XML-RPC response on the specified channel, targeting the given message ID, with string and integer payload data.


## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `uuid` | XML-RPC channel ID. |
| `message_id` | `uuid` | XML-RPC message ID. |
| `sdata` | `string` | String payload data to reply with. |
| `idata` | `number` | Integer payload data to reply with. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `script_communication` |