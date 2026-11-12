# `ll.GetAlpha`

```lua
ll.GetAlpha(face: number) -> number
```

Returns a floating-point value indicating the Blinn-Phong alpha (transparency) for the specified face. When the face parameter is set to ALL_SIDES, it computes and returns the average alpha value across all faces.

## Arguments

| Name | Type | Description |
|---|---|---|
| `face` | number | Face number or ALL_SIDES. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim`, `prim_appearance` |
