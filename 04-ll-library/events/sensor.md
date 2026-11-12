# `sensor`

```lua
sensor(detected: {DetectedEvent}) -> ()
```

This function executes when surrounding objects meet the criteria set by `ll.Sensor` or `ll.SensorRepeat`. The handler receives a collection detailing all identified targets.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | A collection of event objects, with each entry providing details about an identified agent or object. You can access properties like its name and position from every element. |

**Returns:** `()`
