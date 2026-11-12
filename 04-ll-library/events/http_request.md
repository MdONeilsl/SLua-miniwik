# `http_request`

```lua
http_request(request_id: uuid, method: string, body: string) -> ()
```

This handler executes whenever a client sends an HTTP call to the script's designated endpoint. It provides details about the connection and data received by the system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `request_id` | `uuid` | The unique identifier assigned to this specific network call. |
| `method` | `string` | Specifies the action type, such as GET or POST. |
| `body` | `string` | The textual data contained within the incoming message payload. |

**Returns:** `()`
