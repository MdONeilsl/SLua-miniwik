# `ll.LoopSound`

```lua
ll.LoopSound(sound: string | uuid, volume: number) -> ()
```

This function plays a sound continuously in a loop at the given volume. A prim may only have one sound attached at any time; when a new loop is initiated, it modifies the volume of the existing sound without interrupting playback.

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