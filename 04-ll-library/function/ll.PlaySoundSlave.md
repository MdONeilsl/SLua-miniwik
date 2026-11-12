# `ll.PlaySoundSlave`

```lua
ll.PlaySoundSlave(sound: string | uuid, volume: number) -> ()
```

Plays the specified sound once at the given volume, aligned with the next loop point of the currently most audible active Sync Master.


## Arguments

| Name | Type | Description |
|---|---|---|
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
