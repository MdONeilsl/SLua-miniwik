# `ll.RezObject`

```lua
ll.RezObject(item: string, pos: vector, vel: vector, rot: quaternion, start_param: number) -> ()
```

Creates and places the specified inventory item at the given position, oriented and moving according to the provided rotation and velocity, while passing the start parameter to its on_rez event; velocity is disregarded if the object is non-physical.


## Arguments

| Name | Type | Description |
|---|---|---|
| `item` | `string` | Name of the object in the prim's inventory to rez. |
| `pos` | `vector` | Position vector in region coordinates where the center of the object will be placed. |
| `vel` | `vector` | Initial velocity vector (maximum magnitude ~200m/s). |
| `rot` | `quaternion` | Initial rotation of the rezzed object. |
| `start_param` | `number` | Start parameter passed to the rezzed object's on_rez event (accessible via ll.GetStartParameter). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `200.0` |
| `sleep` | `0.1` |
| `categories` | `prim_inventory`, `rez` |