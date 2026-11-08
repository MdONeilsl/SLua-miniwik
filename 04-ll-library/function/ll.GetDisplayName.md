# `ll.GetDisplayName`

```lua
ll.GetDisplayName(id: uuid) -> string
```

If the specified avatar is present in the region or has a cached display name, this function returns the corresponding string; otherwise, it returns an empty string, and you should use ll.RequestDisplayName to retrieve the name when the avatar is not available.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar in the same region or otherwise known to the region. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |