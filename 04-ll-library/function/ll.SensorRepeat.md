# `ll.SensorRepeat`

```lua
ll.SensorRepeat(name: string, id: uuid, type: number, radius: number, arc: number, rate: number) -> ()
```

Configures a recurring scan that occurs at intervals defined by rate, searching for objects or avatars matching the specified type, name, and ID within a given radius and angular arc relative to the forward direction. Detected entities will trigger sensor or no_sensor events.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | Specific object or avatar name to filter for (or empty string for no filter). |
| `id` | `uuid` | UUID of the group, avatar, or object to filter by (or NULL_KEY for no filter). |
| `type` | `number` | — |
| `radius` | `number` | Maximum distance in meters to scan (range [0.0, 96.0]). |
| `arc` | `number` | Maximum angle in radians relative to the local X-axis to scan (range [0.0, PI]). |
| `rate` | `number` | Interval in seconds between repeated scans. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sensor` |