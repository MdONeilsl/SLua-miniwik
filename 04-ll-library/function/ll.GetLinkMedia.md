# `ll.GetLinkMedia`

```lua
ll.GetLinkMedia(link: number, face: number, params: {number}) -> {any}
```

For the given link and face, this function retrieves media parameters in the sequence specified by the params list, returning them as a list.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `face` | `number` | Face number (side) of the prim. |
| `params` | `{number}` | A list of PRIM_MEDIA_* property constants to retrieve values for. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `media`, `prim_media` |
