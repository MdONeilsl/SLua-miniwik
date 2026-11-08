# `ll.GetPrimMediaParams`

```lua
ll.GetPrimMediaParams(face: number, params: {number}) -> {any}
```

For the given face, this function returns a list of media parameters in the sequence specified by the params list. If no media is present on that face, it returns an empty list.

## Arguments

| Name | Type | Description |
|---|---|---|
| `face` | number | Face number (side) of the prim. |
| `params` | {number} | A list of PRIM_MEDIA_* property constants to retrieve values for. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `media`, `prim`, `prim_media` |