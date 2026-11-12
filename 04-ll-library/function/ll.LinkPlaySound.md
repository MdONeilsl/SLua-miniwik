# `ll.LinkPlaySound`

```lua
ll.LinkPlaySound(link: number, sound: string | uuid, volume: number, flags: number) -> ()
```

Activates the designated sound on the specified prim link, either as a single play or in a loop, adjusted to the given volume. A prim can only have one sound playing at any time; initiating a new sound or invoking ll.StopSound will terminate the currently playing sound. Playback behavior is governed by the flags parameter.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |
| `flags` | `number` | Bitwise flags (combination of SOUND_*) controlling the sound playback. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
