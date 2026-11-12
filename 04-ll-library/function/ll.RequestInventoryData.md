# `ll.RequestInventoryData`

```lua
ll.RequestInventoryData(item: string) -> uuid
```

Initiates an asynchronous request for data associated with the specified inventory item, which in turn triggers a dataserver event. At present, this function supports only landmark items (which provide local region coordinates). The function returns a key used to handle the query.


## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the item in the prim's inventory. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `dataserver`, `prim_inventory` |
