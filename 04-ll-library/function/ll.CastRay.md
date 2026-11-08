# `ll.CastRay`

```lua
ll.CastRay(start_pos: vector, end_pos: vector, options: list) -> {any}
```

Emits a ray through the physics environment from the specified start to end point, detecting collisions with objects according to provided options. The result is a list of interleaved values in the format [UUID_1, {link_number_1}, hit_position_1, {hit_normal_1}, ..., status_code], where a negative status_code signals an error and a non-negative value indicates the count of collision events.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start_pos` | `vector` | Starting location vector of the ray. |
| `end_pos` | `vector` | Ending location vector of the ray. |
| `options` | `list` | A list of option flags and their parameters to configure the raycast. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `sensor` |