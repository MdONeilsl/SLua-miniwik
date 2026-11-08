# `ll.SetInventoryPermMask`

```lua
ll.SetInventoryPermMask(item: string, group: number, flags: number) -> ()
```

Assigns the given permission flags to the specified item for the designated group.


## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the item in the prim's inventory. |
| `group` | `number` | MASK_* group (e.g., MASK_BASE, MASK_OWNER, MASK_GROUP, MASK_EVERYONE, or MASK_NEXT) to set. |
| `flags` | `number` | Bitfield of permissions (PERM_* flags) to set. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `asset_permissions`, `prim_inventory` |