# `ll.GetAttachedList`

```lua
ll.GetAttachedList(avatar: uuid) -> {uuid} | {string}
```

This function retrieves a list of UUIDs representing objects worn by the given avatar, ordered by the sequence in which they were attached. HUDs are excluded since they are not publicly accessible or visible. On failure, it returns a list with a single error message string.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar in the same region. |

**Returns:** `{uuid} | {string}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `attachments`, `avatar` |
