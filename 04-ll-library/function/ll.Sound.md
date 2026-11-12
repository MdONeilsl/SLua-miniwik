# `ll.Sound`

```lua
ll.Sound(sound: string | uuid, volume: number, queue: boolean | number, loop: boolean | number) -> ()
```

This function is deprecated; use ll.PlaySound instead. It plays a designated sound at a specified volume, with the ability to either loop the sound or queue it for playback.

## Arguments

| Name | Type | Description |
|---|---|---|
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |
| `queue` | `boolean | number` | Boolean. If TRUE, queues the sound; if FALSE, interrupts the currently playing sound. |
| `loop` | `boolean | number` | Boolean. If TRUE, loops the sound. |

**Returns:** `()`

## Deprecated

- **use:** ll.PlaySound

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
