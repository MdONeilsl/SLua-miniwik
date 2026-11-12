# `ll.GetInventoryPermMask`

```lua
ll.GetInventoryPermMask(item: string, group: number) -> number
```

For the given item in the prim's inventory, this function retrieves the permission flags associated with the specified group.

## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the item in the prim's inventory. |
| `group` | `number` | MASK_* group (e.g., MASK_BASE, MASK_OWNER, MASK_GROUP, MASK_EVERYONE, or MASK_NEXT) to get. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `asset_permissions`, `prim_inventory` |
