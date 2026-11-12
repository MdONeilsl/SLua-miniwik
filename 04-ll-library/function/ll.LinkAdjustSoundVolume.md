# `ll.LinkAdjustSoundVolume`

```lua
ll.LinkAdjustSoundVolume(link: number, volume: number) -> ()
```

Modifies the volume of the sound currently playing on the specified prim link (does not affect sounds initiated via ll.TriggerSound).


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag of the prim to adjust. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
