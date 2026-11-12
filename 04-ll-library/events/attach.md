# `attach`

```lua
attach(avatar: uuid) -> ()
```

This event fires when the object's attachment status changes relative to an avatar. The function receives the UUID of the attached user, or a specific key if no user is connected.

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | The unique identifier for the user connected to this object, or a specific key when disconnected. |

**Returns:** `()`
