# `ll.SetLinkRenderMaterial`

```lua
ll.SetLinkRenderMaterial(link: number, material: string | uuid, face: number) -> ()
```

Assigns a specified material, either by its UUID or inventory name, to a particular face of a linked primitive. Important: This operation resets most PRIM_GLTF_* properties on that face, with the exception of repeats, offsets, and rotation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `material` | `string | uuid` | Name of a material in the prim's inventory, or a UUID. |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `linkset`, `prim_appearance` |