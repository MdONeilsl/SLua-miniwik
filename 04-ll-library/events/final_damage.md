# `final_damage`

```lua
final_damage(detected: {DetectedEvent}) -> ()
```

This event executes after all damage calculations are complete, applying any resulting harm either directly to the wearer or distributing it among seated avatars. Functions for collision detection (ll.Detected*) and ll.DetectedDamage remain available during this time.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | A collection of event data records, each detailing an object or agent found nearby. |

**Returns:** `()`
