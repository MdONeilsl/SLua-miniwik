# `ll.GiveInventoryList`

```lua
ll.GiveInventoryList(target: uuid, folder: string, items: {string}) -> ()
```

Transfers a list of inventory items to the specified target, organizing them into a new folder with the given name. If the target is an object, the items are added directly to its inventory without creating a folder. The target must be either an agent or an object located within the same region.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target agent or prim in the same region. |
| `folder` | `string` | Name of the destination folder to be created (ignored if the target is an object). |
| `items` | `{string}` | The names of the items in the prim's inventory to transfer. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `avatar_inventory`, `prim_inventory` |
