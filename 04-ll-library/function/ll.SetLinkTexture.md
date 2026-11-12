# `ll.SetLinkTexture`

```lua
ll.SetLinkTexture(link: number, texture: string | uuid, face: number) -> ()
```

Assigns a specified texture, either by its UUID or inventory name, to a particular face of a prim linked to the current object.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `texture` | `string | uuid` | Name of a texture in the prim's inventory, or a UUID. |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `linkset`, `prim_appearance` |
