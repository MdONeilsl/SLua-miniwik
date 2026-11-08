# `ll.MapBeacon`

```lua
ll.MapBeacon(region_name: string, pos: vector, options: list) -> ()
```

Shows a beacon within the game world, which may also launch the world map when an avatar interacts with or wears the object, with the beacon centered on the specified region and highlighting the given position. This function is restricted to use within attached scripts or during touch events.


## Arguments

| Name | Type | Description |
|---|---|---|
| `region_name` | `string` | Name of the region where the beacon is displayed. |
| `pos` | `vector` | Position vector in region coordinates to highlight. |
| `options` | `list` | A list of options to configure the map beacon. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `avatar_communication`, `user_interface` |