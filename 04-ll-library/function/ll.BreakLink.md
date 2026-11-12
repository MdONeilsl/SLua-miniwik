# `ll.BreakLink`

```lua
ll.BreakLink(link: number) -> ()
```

Removes the specified prim from the link set using its link number. This operation necessitates the PERMISSION_CHANGE_LINKS runtime permission.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | The link number (0: unlinked, 1: root prim, >1: child prims and seated avatars) to delink. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset` |
