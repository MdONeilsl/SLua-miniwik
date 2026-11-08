# `ll.SetLinkColor`

```lua
ll.SetLinkColor(link: number, color: vector, face: number) -> ()
```

Assigns the diffuse RGB color using the Blinn-Phong model to the specified face on the prim linked via the given link number.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `color` | `vector` | Color vector in RGB <R, G, B> (values from 0.0 to 1.0). |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |