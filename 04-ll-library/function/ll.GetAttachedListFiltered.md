# `ll.GetAttachedListFiltered`

```lua
ll.GetAttachedListFiltered(avatar: uuid, options: list) -> {uuid} | {string}
```

This function retrieves a list of UUIDs representing objects worn by the given avatar, ordered by the sequence in which they were attached, with filtering applied based on the provided options. If the operation fails, it returns a list containing a single error message string.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar in the same region. |
| `options` | `list` | A list of options to filter the returned attachments. |

**Returns:** `{uuid} | {string}`

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | attachments, avatar |