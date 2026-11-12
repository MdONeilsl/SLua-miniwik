# `ll.NavigateTo`

```lua
ll.NavigateTo(pos: vector, options: list) -> ()
```

Initiates pathfinding for a character to move toward the specified position pos, which may be within the current region or an adjacent one, by applying the configuration settings found in options.


## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Destination position vector in region coordinates. |
| `options` | `list` | A list of parameters to configure pathfinding behavior (currently only FORCE_DIRECT_PATH is supported). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |
