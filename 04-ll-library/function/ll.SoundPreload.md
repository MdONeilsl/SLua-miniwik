# `ll.SoundPreload`

```lua
ll.SoundPreload(sound: string | uuid) -> ()
```

This function is obsolete; use ll.PreloadSound instead. It prepares the designated sound for playback by viewers who are within range.


## Arguments

| Name | Type | Description |
|---|---|---|
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |

**Returns:** `()`

## Deprecated

- **use:** ll.PreloadSound

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
