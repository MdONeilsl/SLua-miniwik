# `ll.LoopSoundMaster`

```lua
ll.LoopSoundMaster(sound: string | uuid, volume: number) -> ()
```

Starts playing the specified sound in an infinite loop at the given volume level and designates it as a synchronization master, ensuring that any slave sounds are locked to its timing.


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
