# `ll.GetGameControlModeButtons`

```lua
ll.GetGameControlModeButtons(id: uuid) -> {any}
```

Returns an integer bitmask representing the currently active modal buttons for the specified avatar’s active game-control mode. The meaning of each bit depends on the current mode; consult the GAME_CONTROL_BUTTON_* constants to interpret the bits.


## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar whose game-controller state to query. |

**Returns:** `integer`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `avatar`, `game_control`, `input` |
| `energy` | `10.0` |
| `sleep` | `0.0` |