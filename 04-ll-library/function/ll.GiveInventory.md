# `ll.GiveInventory`

```lua
ll.GiveInventory(target: uuid, item: string) -> ()
```

Transfers the named inventory item to the specified target, respecting the permissions system. The target may be any active agent or object within the same region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target agent or prim. |
| `item` | `string` | Name of the item in the prim's inventory to transfer. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_inventory`, `prim_inventory` |
