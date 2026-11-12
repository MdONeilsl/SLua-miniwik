# `ll.GetUsername`

```lua
ll.GetUsername(id: uuid) -> string
```

If the specified avatar is connected to the region or has a cached username, this function returns the corresponding string; otherwise, it returns an empty string. Use ll.RequestUsername to obtain the username when the avatar is not present.


## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | uuid | UUID of the avatar in the same region or otherwise known to the region. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |
