# `ll.GetGameControlModeAxes`

```lua
ll.GetGameControlModeAxes(id: uuid) -> {any}
```

This function returns a list of floating-point values corresponding to the active axes in the current game-control mode for the specified avatar. The number of elements and their meaning depend on the mode; refer to the GAME_CONTROL_AXIS_* constants to interpret the indices.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar whose game-controller state to query. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `avatar`, `game_control`, `input` |
| `energy` | `10.0` |
| `sleep` | `0.0` |
