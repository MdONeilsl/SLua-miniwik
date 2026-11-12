# `ll.GiveAgentInventory`

```lua
ll.GiveAgentInventory(agent: uuid, folder: string, items: {string}, options: list) -> number
```

Transfers the listed inventory items to the specified agent, creating a new folder with the given name, subject to permission restrictions. The transfer behavior can be customized via the options parameter.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the target agent in the same region. |
| `folder` | `string` | Name of the destination folder to be created |
| `items` | `{string}` | The names of the items in the prim's inventory to transfer. |
| `options` | `list` | A list of options to configure the inventory transfer. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `avatar_inventory`, `prim_inventory` |
