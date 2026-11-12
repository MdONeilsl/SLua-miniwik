# `collision_start`

```lua
collision_start(detected: {DetectedEvent}) -> ()
```

This event fires when an avatar or object first makes contact with the item holding this script. The handler receives a collection detailing all objects involved in the initial collision.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | Contains information for every object that initiated contact with this script's location. |

**Returns:** `()`
