# `on_damage`

```lua
on_damage(detected: {DetectedEvent}) -> ()
```

This event executes when damage has been dealt to an object or avatar, prior to its final application. Developers can utilize functions like `ll.DetectedDamage` and related collision detection methods within the handler.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | A table containing event data for each impacted agent or object. |

**Returns:** `()`
