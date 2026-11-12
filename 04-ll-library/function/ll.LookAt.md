# `ll.LookAt`

```lua
ll.LookAt(target: vector, strength: number, damping: number) -> ()
```

Makes the object rotate so its positive Z-axis (up direction) points toward the specified target vector, while ensuring its positive X-axis (forward direction) remains below the horizon. Continues tracking the target until ll.StopLookAt is invoked or the strength parameter is adjusted to 0.0.


## Arguments

| Name | Type | Description |
|---|---|---|
| target | vector | Target position vector in region coordinates to look at. |
| strength | number | Force of rotation (0.0 cancels the tracking; values around half the object's mass are typical). |
| damping | number | Timescale in seconds to critically damp the orientation. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | movement, physics |
