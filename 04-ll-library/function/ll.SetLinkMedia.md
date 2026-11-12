# `ll.SetLinkMedia`

```lua
ll.SetLinkMedia(link: number, face: number, params: list | MediaParams) -> number
```

Applies the media settings defined in params to the specified face of the linked prim immediately, without waiting for a script delay. Returns an integer STATUS_* value indicating whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `face` | `number` | Face number (side) of the prim. |
| `params` | `list | MediaParams` | A set of property-value pairs (in no particular order) specifying media parameters, or a PrimMediaParams dictionary. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `media`, `prim_media`, `web` |
