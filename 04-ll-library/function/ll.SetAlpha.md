# `ll.SetAlpha`

```lua
ll.SetAlpha(alpha: number, face: number) -> ()
```

Configures the alpha (transparency) of the diffuse texture for the specified face; when face is set to ALL_SIDES, the effect is applied uniformly across all faces. The alpha value is constrained to a range between 0.1 and 1.0, inclusive, with 1.0 representing full opacity.

## Arguments

| Name | Type | Description |
|---|---|---|
| `alpha` | number | Transparency value to set, from 0.0 (clear) to 1.0 (solid; clamped to a minimum of 0.1). |
| `face` | number | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim`, `prim_appearance` |