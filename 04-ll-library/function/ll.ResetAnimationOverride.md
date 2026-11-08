# `ll.ResetAnimationOverride`

```lua
ll.ResetAnimationOverride(anim_state: string) -> ()
```

Restores the default animation override for the specified anim_state (use 'ALL' to reset all states). This function necessitates the PERMISSION_OVERRIDE_ANIMATIONS permission.


## Arguments

| Name | Type | Description |
|---|---|---|
| `anim_state` | `string` | Animation state string (or 'ALL') to reset. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_animation`, `permissions` |