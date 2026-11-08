# `ll.OpenFloater`

```lua
ll.OpenFloater(floater_name: string, url: string, params: list) -> number
```

Launches a viewer floater identified by floater_name, loading the given url and applying the specified params. The function returns an integer indicating success (0) or an error code.

## Arguments

| Name | Type | Description |
|---|---|---|
| `floater_name` | `string` | Identifier string of the viewer floater to open. |
| `url` | `string` | URL to load within the opened floater. |
| `params` | `list` | Options or parameters to apply to the opened floater. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication` |