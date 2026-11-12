# `ll.LoadURL`

```lua
ll.LoadURL(avatar: uuid, message: string, url: string) -> ()
```

Displays a dialog to the specified avatar, presenting the given message and prompting them to confirm opening the provided URL in their default web browser upon selection.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | uuid | UUID of the avatar in the same region. |
| `message` | string | Text message to display in the dialog box. |
| `url` | string | Web URL to open. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `avatar_communication`, `user_interface`, `web` |
