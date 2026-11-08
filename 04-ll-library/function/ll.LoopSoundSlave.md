# `ll.LoopSoundSlave`

```lua
ll.LoopSoundSlave(sound: string | uuid, volume: number) -> ()
```

Repeats the specified sound continuously at the given volume, aligned with the closest active Sync Master that is currently audible.


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