# `ll.ScaleTexture`

```lua
ll.ScaleTexture(u: number, v: number, face: number) -> ()
```

Adjusts the horizontal and vertical scaling of the diffuse texture on the designated face of the prim, with negative values causing the texture to flip. When face is set to ALL_SIDES, the effect applies to all faces.

## Arguments

| Name | Type | Description |
|---|---|---|
| u | number | Horizontal (U) texture repeats scale value, in the interval [-100.0, 100.0]. |
| v | number | Vertical (V) texture repeats scale value, in the interval [-100.0, 100.0]. |
| face | number | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `prim`, `prim_appearance` |
