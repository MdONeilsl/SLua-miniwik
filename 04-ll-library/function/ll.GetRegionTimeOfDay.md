# `ll.GetRegionTimeOfDay`

```lua
ll.GetRegionTimeOfDay() -> number
```

Returns a floating-point value with subsecond accuracy indicating the number of seconds that have passed since either the region’s environmental midnight or its uptime, whichever occurs first. When the region’s sun position is fixed, it returns the region’s uptime instead.

## Arguments

_No arguments._

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `region`, `time` |