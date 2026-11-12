# `http_response`

```lua
http_response(request_id: uuid, status: number, metadata: {any}, body: string) -> ()
```

This function executes when data arrives for a previously sent query, whether that query succeeded, failed, or timed out.

## Arguments

| Name | Type | Description |
|---|---|---|
| `request_id` | `uuid` | The identifier corresponding to the initial request call. |
| `status` | `number` | The numerical HTTP response code received. |
| `metadata` | `{any}` | Collection of response headers and HTTP constants. |
| `body` | `string` | The actual content received in the response. |

**Returns:** `()`
