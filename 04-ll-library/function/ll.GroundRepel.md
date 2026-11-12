# `ll.GroundRepel`

```lua
ll.GroundRepel(height: number, water: boolean | number, tau: number) -> ()
```

When the object is within half the specified height of the terrain (or water level if water is true), this function applies critical damping to its vertical movement, using the given tau value as the damping timescale. It operates only on objects with physics enabled and is not compatible with vehicles.

## Arguments

| Name | Type | Description |
|---|---|---|
| `height` | `number` | Target distance in meters above the ground or water. |
| `water` | `boolean | number` | Boolean. If TRUE, damp relative to the higher of land and water; if FALSE, damp relative to land only. |
| `tau` | `number` | Timescale in seconds to critically damp the movement. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `region` |
