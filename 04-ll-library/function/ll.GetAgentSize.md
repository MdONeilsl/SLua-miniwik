# `ll.GetAgentSize`

```lua
ll.GetAgentSize(avatar: uuid) -> vector
```

Returns a vector that indicates the approximate bounding box dimensions of the given avatar, or ZERO_VECTOR if the avatar is not located in the same region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar in the same region. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |