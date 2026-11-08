# `ll.GetGameControlMode`

```lua
ll.GetGameControlMode(id: uuid) -> number
```

Returns an integer value from the GAME_CONTROL_MODE_* constants that represents the active game-control mode for the specified avatar, identified by its UUID.


## Arguments

| Name | Type | Description |
|---|---|---|
| id | uuid | UUID of the avatar whose game-controller state to query. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| categories | avatar, game_control, input |
| energy | 10.0 |
| sleep | 0.0 |