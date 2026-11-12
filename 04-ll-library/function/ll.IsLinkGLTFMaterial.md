# `ll.IsLinkGLTFMaterial`

```lua
ll.IsLinkGLTFMaterial(link: number, face: number) -> boolean
```

Determines whether the material on the specified face of the linked prim uses a physically-based rendering (PBR) model, returning TRUE, or falls back to a Blinn-Phong diffuse shading model, returning FALSE.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (or LINK_* flag) of the prim to inspect. |
| `face` | `number` | Face number (or ALL_SIDES) of the prim to inspect. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |
