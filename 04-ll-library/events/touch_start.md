# `touch_start`

```lua
touch_start(detected: {DetectedEvent}) -> ()
```

Fires when a user press their left mouse button while the cursore is over the object. The function provides details about all touching avatars.

## Arguments

| Name | Type | Description |
|---|---|---|
| `detected` | `{DetectedEvent}` | A collection of events detailing every agent or object that touched this prim. Each entry provides access to key data like position and name. |

**Returns:** `()`
