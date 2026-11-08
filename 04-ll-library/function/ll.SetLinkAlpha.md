# `ll.SetLinkAlpha`

```lua
ll.SetLinkAlpha(link: number, alpha: number, face: number) -> ()
```

Applies the specified transparency level to the designated face of the prim linked via the given link number.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `alpha` | `number` | Transparency value to set, from 0.0 (clear) to 1.0 (solid). |
| `face` | `number` | Face number or ALL_SIDES. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |