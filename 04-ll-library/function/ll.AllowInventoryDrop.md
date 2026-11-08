# `ll.AllowInventoryDrop`

```lua
ll.AllowInventoryDrop(add: boolean | number) -> ()
```

When add is set to TRUE, it permits users lacking object modify permissions to drop inventory items onto the prim. When add is FALSE, only users holding modify permissions are allowed to drop inventory items onto the prim.

## Arguments

| Name | Type | Description |
|---|---|---|
| `add` | `boolean | number` | Boolean. If TRUE, allows anyone to drop inventory items into the prim (even without modify rights). If FALSE, restricts inventory dropping to those with modify permissions. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim_inventory` |