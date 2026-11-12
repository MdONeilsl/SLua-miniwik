# `ll.SendRemoteData`

```lua
ll.SendRemoteData(channel: uuid, dest: string, idata: number, sdata: string) -> uuid
```

This function is obsolete and transmits an XML-RPC request to the specified destination using the given channel, encapsulating the channel ID as a string, an integer value, and a string payload. It returns a key that identifies the message.


## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `uuid` | XML-RPC channel ID. |
| `dest` | `string` | Destination XML-RPC URL or server. |
| `idata` | `number` | Integer payload data. |
| `sdata` | `string` | String payload data. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `script_communication` |
