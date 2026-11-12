# `ll.SetLinkGLTFOverrides`

```lua
ll.SetLinkGLTFOverrides(link: number, face: number, params: list) -> ()
```

Applies or clears specific GLTF override parameters defined in the params list to the designated face of the prim linked via the specified link.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `face` | `number` | Face number or ALL_SIDES. |
| `params` | `list` | A list of overrides and their corresponding values to set. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |
