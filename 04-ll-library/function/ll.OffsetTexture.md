# `ll.OffsetTexture`

```lua
ll.OffsetTexture(u: number, v: number, face: number) -> ()
```

Applies horizontal (U) and vertical (V) texture offsets to the specified face; when face is set to ALL_SIDES, the offsets are applied uniformly across all faces.

## Arguments

| Name | Type | Description |
|---|---|---|
| `u` | `number` | Horizontal (U) offset, typically in the interval [-1.0, 1.0]. |
| `v` | `number` | Vertical (V) offset, typically in the interval [-1.0, 1.0]. |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `prim`, `prim_appearance` |
