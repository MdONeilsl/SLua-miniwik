# `ll.HTTPResponse`

```lua
ll.HTTPResponse(request_id: uuid, status: number, body: string) -> ()
```

Sends a response to the specified HTTP request, using the given status code and response body content.


## Arguments

| Name | Type | Description |
|---|---|---|
| `request_id` | `uuid` | Unique key identifying the incoming HTTP request. |
| `status` | `number` | Integer HTTP status code (such as 200, 400, or 404) to respond with. |
| `body` | `string` | String contents of the response body. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `media`, `prim_media`, `script_communication`, `web` |
