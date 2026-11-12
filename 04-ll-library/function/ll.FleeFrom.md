# `ll.FleeFrom`

```lua
ll.FleeFrom(position: vector, distance: number, options: list) -> ()
```

Causes a pathfinding character to maintain a specified distance from a given position vector, operating within the current region or neighboring regions.

## Arguments

| Name | Type | Description |
|---|---|---|
| `position` | `vector` | Position vector in region coordinates from which to flee. |
| `distance` | `number` | Distance in meters to keep from the position. |
| `options` | `list` | No options currently available (should be empty list). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |
