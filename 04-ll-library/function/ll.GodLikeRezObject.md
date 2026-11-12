# `ll.GodLikeRezObject`

```lua
ll.GodLikeRezObject(id: uuid, pos: vector) -> ()
```

Places an object at the specified position using its UUID, but only if the owner possesses the god-mode permission.


## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | Asset UUID of the object to rez. |
| `pos` | `vector` | Position vector in region coordinates where the object will be rezzed. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim_inventory`, `rez` |
