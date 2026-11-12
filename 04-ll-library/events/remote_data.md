# `remote_data`

**Deprecated.**

```lua
remote_data(event_type: number, channel: uuid, message_id: uuid, sender: string, idata: number, sdata: string) -> ()
```

This function executes when data arrives via an XML-RPC mechanism, providing details such as the event type, sending entity, and associated payload values.

## Arguments

| Name | Type | Description |
|---|---|---|
| `event_type` | `number` | The numeric code indicating the specific kind of remote procedure call event. |
| `channel` | `uuid` | Identifies the communication channel used by the XML-RPC system. |
| `message_id` | `uuid` | Unique identifier for the incoming remote procedure call message. |
| `sender` | `string` | The name or unique label of the entity that initiated the call. |
| `idata` | `number` | A numerical value included in the data payload. |
| `sdata` | `string` | Textual information carried within the data payload. |

**Returns:** `()`
