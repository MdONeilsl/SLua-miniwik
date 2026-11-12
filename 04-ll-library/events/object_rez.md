# `object_rez`

```lua
object_rez(id: uuid) -> ()
```

This function fires when the current object manages to spawn a different item stored within its own inventory. The handler receives the unique identifier for the newly created object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | The unique identifier for the item that was just spawned. |

**Returns:** `()`
