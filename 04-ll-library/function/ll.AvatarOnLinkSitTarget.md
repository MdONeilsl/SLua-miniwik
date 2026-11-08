# `ll.AvatarOnLinkSitTarget`

```lua
ll.AvatarOnLinkSitTarget(link: number) -> uuid
```

Returns the unique identifier of the avatar currently seated on the sit target of the specified link, or NULL_KEY if no avatar is present.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Index of the prim in the linkset (1 for root, >1 for children), or a LINK_* flag. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `linkset`, `sit` |