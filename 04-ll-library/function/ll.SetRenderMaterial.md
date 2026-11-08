# `ll.SetRenderMaterial`

```lua
ll.SetRenderMaterial(material: string | uuid, face: number) -> ()
```

Assigns a material, specified by its UUID or inventory name, to a given face of the prim. Important: This operation resets nearly all PRIM_GLTF_* properties on that face, with the exception of repeats, offsets, and rotation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `material` | `string | uuid` | Name of a material in the prim's inventory, or a UUID. |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `prim`, `prim_appearance` |