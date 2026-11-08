# `ll.SetPrimMediaParams`

```lua
ll.SetPrimMediaParams(face: number, params: list | MediaParams) -> number
```

Applies the media settings defined in params to the specified face of the prim. The function returns an integer STATUS_* value indicating whether the operation succeeded or failed.


## Arguments

| Name | Type | Description |
|---|---|---|
| `face` | `number` | Face number (side) of the prim. |
| `params` | `list | MediaParams` | A set of property-value pairs (in no particular order) specifying media parameters. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `media`, `prim`, `prim_media`, `web` |