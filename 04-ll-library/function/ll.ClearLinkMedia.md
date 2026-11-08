# `ll.ClearLinkMedia`

```lua
ll.ClearLinkMedia(link: number, face: number) -> number
```

Removes the media and resets all associated parameters for the specified face on the linked prim. The function returns an integer STATUS_* value indicating whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | The link number (0: unlinked, 1: root prim, >1: child prims) or a LINK_* flag representing the target prim. |
| `face` | `number` | Face number to clear. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `media`, `prim_media` |