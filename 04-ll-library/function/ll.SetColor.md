# `ll.SetColor`

```lua
ll.SetColor(color: vector, face: number) -> ()
```

Applies the specified RGB color to the given face using the Blinn-Phong diffuse model; when face is set to ALL_SIDES, the color is applied uniformly across all faces.


## Arguments

| Name | Type | Description |
|---|---|---|
| `color` | `vector` | Color vector in RGB <R, G, B> (values from 0.0 to 1.0). |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim`, `prim_appearance` |