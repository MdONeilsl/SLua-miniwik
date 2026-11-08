# `ll.HTTPRequest`

```lua
ll.HTTPRequest(url: string, parameters: list | HttpRequestParams, body: string) -> uuid
```

Initiates an HTTP request to the given URL, incorporating the specified body and configuration parameters. Triggers an http_response event upon completion and returns a unique key handle to reference the request.

## Arguments

| Name | Type | Description |
|---|---|---|
| `url` | `string` | Destination HTTP or HTTPS URL. |
| `parameters` | `list | HttpRequestParams` | A list of HTTP_* configuration flags and value pairs, or an HTTPRequestParams dictionary. |
| `body` | `string` | String contents of the request body. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `script_communication`, `web` |