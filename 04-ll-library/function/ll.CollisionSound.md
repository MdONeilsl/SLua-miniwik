# `ll.CollisionSound`

```lua
ll.CollisionSound(impact_sound: string | uuid, impact_volume: number) -> ()
```

Disables the default collision audio and substitutes it with the specified impact_sound at the given impact_volume level. Using an empty string will disable all collision sounds without playing any replacement.

## Arguments

| Name | Type | Description |
|---|---|---|
| `impact_sound` | `string | uuid` | UUID of a sound, the name of a sound in the prim's inventory, or an empty string to suppress sounds. |
| `impact_volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `sound` |
