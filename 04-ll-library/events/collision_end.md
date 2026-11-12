# `collision_end`

```lua
collision_end(detected: {DetectedEvent}) -> ()
```

This function executes when an attached object ceases physical contact with another entity or avatar. It provides data regarding all objects that were previously in collision.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | A collection of event objects, where each entry represents an agent or object detected during the collision. You can access details like position, name, and key for every item within this set. |

**Returns:** `()`
