# `ll.Sensor`

```lua
ll.Sensor(name: string, id: uuid, type: number, radius: number, arc: number) -> ()
```

Executes a one-time scan in the direction the prim is facing, detecting objects or avatars matching a specified name, type, and ID within a given radius and angular arc. Detected entities trigger either a sensor or no_sensor event. Omitting any filter condition—by providing an empty string for name, zero for type, or NULL_KEY for ID—disables that particular filter.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | Specific object or avatar name to filter for (or empty string for no filter). |
| `id` | `uuid` | UUID of the group, avatar, or object to filter by (or NULL_KEY for no filter). |
| `type` | `number` | |
| `radius` | `number` | Maximum distance in meters to scan (range [0.0, 96.0]). |
| `arc` | `number` | Maximum angle in radians relative to the local X-axis to scan (range [0.0, PI]). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sensor` |