# `ll.TriggerSoundLimited`

```lua
ll.TriggerSoundLimited(sound: string | uuid, volume: number, top_north_east: vector, bottom_south_west: vector) -> ()
```

Emits the specified sound once at the given volume, positioned relative to the object’s center but not affixed to it, confined within an axis-aligned bounding box determined by the top-north-east and bottom-south-west coordinates.

## Arguments

| Name | Type | Description |
|---|---|---|
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |
| `top_north_east` | `vector` | Top-north-east boundary position vector in region coordinates. |
| `bottom_south_west` | `vector` | Bottom-south-west boundary position vector in region coordinates. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
