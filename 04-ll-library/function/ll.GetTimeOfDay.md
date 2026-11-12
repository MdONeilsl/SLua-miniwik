# `ll.GetTimeOfDay`

```lua
ll.GetTimeOfDay() -> number
```

Returns a floating-point value with subsecond accuracy indicating the number of seconds that have passed since either the parcel’s environmental midnight or the region’s uptime, whichever occurs first. When the parcel’s sun position is fixed, the function returns the region’s uptime instead.


## Arguments

_No arguments._

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `time` |
