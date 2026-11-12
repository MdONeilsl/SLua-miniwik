# `ll.PlaySound`

```lua
ll.PlaySound(sound: string | uuid, volume: number) -> ()
```

When invoked, this function plays the designated sound at the specified volume, bound to the object. At any given time, only a single sound may be active per prim; subsequent calls with new sounds or invoking ll.StopSound will terminate the current playback. If the same sound is called again, its volume is adjusted without interrupting playback.

## Arguments

| Name | Type | Description |
|---|---|---|
| sound | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| volume | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
