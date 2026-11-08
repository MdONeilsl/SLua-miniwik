# `ll.GetColor`

```lua
ll.GetColor(face: number) -> vector
```

Returns the RGB color vector in Blinn-Phong shading for the specified face, with each component ranging from 0.0 to 1.0. When the face parameter is set to ALL_SIDES, the function returns the average color across all faces.


## Arguments

| Name | Type | Description |
|---|---|---|
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim`, `prim_appearance` |