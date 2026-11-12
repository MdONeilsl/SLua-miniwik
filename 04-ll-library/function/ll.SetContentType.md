# `ll.SetContentType`

```lua
ll.SetContentType(request_id: uuid, content_type: number) -> ()
```

Configures the 'Content-Type' HTTP header for responses associated with the given request_id, using the specified content_type, which must be one of the CONTENT_TYPE_* constants.


## Arguments

| Name | Type | Description |
|---|---|---|
| `request_id` | uuid | Unique key identifying the incoming HTTP request. |
| `content_type` | number | CONTENT_TYPE_* constant representing the Internet media type to use. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `media`, `prim_media`, `web` |
