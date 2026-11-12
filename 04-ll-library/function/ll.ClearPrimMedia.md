# `ll.ClearPrimMedia`

```lua
ll.ClearPrimMedia(face: number) -> number
```

Removes the media content and resets all associated parameters for the given face. The function returns an integer STATUS_* value indicating whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `face` | `number` | Face number (side) to clear. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `media`, `prim`, `prim_media` |
