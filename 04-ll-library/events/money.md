# `money`

```lua
money(id: uuid, amount: number) -> ()
```

This function executes whenever a specific resident, identified by their UUID, contributes Linden dollars to the object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | The unique identifier for the person who paid. |
| `amount` | `number` | The total number of Linden dollars contributed. |

**Returns:** `()`
