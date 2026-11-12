# `game_control`

```lua
game_control(id: uuid, button_levels: number, axes: {number}) -> ()
```

This event fires when an attached or seated script detects changes to a compatible viewer's game controller input for the specified avatar.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | The unique identifier for the controlling avatar. |
| `button_levels` | `number` | Bitmask showing which standard buttons are pressed. |
| `axes` | `{number}` | Six floating-point values for standard directional input. |

**Returns:** `()`
