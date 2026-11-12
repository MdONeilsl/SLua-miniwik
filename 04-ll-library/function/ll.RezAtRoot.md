# `ll.RezAtRoot`

```lua
ll.RezAtRoot(item: string, pos: vector, vel: vector, rot: quaternion, start_param: number) -> ()
```

Creates and places the specified inventory item at the given position, assigning it the specified initial velocity, rotation, and start parameter for its on_rez event; if the object is non-physical, the velocity is disregarded.

## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the object in the prim's inventory to rez. |
| `pos` | `vector` | Position vector in region coordinates where the root of the object will be placed. |
| `vel` | `vector` | Initial velocity vector for the rezzed object. |
| `rot` | `quaternion` | Initial rotation of the rezzed object. |
| `start_param` | `number` | Start parameter passed to the rezzed object's on_rez event (accessible via ll.GetStartParameter). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `200.0` |
| `sleep` | `0.1` |
| `categories` | `prim_inventory`, `rez` |
