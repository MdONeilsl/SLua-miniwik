# `ll.MapDestination`

```lua
ll.MapDestination(simname: string, pos: vector, look_at: vector) -> ()
```

When an avatar interacts with or wears the object, this function opens the world map focused on the specified simname, with the given pos marked. It is restricted to use within attached scripts or during touch events. The look_at parameter is currently ignored.

## Arguments

| Name | Type | Description |
|---|---|---|
| `simname` | `string` | Name of the target simulator region. |
| `pos` | `vector` | Position vector in region coordinates to highlight. |
| `look_at` | `vector` | Position in local coordinates (currently unused/ignored). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `avatar_communication`, `teleport`, `user_interface` |
