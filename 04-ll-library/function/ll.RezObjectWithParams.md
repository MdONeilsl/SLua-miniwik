# `ll.RezObjectWithParams`

```lua
ll.RezObjectWithParams(item: string, options: list) -> uuid
```

Creates and places the specified object from the rezzing prim's inventory, positioning it at the prim’s location by default unless the REZ_POS flag is included in the options. The initial properties are set using the provided options list. The function returns the unique key of the newly rezzed object, or an empty key if the operation fails.

## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the object in the prim's inventory to rez. |
| `options` | `list` | A list of REZ_* options to configure the rezzed object's attributes. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `200.0` |
| `sleep` | `0.1` |
| `categories` | `combat`, `prim_inventory`, `rez` |