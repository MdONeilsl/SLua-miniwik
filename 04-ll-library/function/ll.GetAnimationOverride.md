# `ll.GetAnimationOverride`

```lua
ll.GetAnimationOverride(anim_state: string) -> string
```

Returns the name of the animation that is currently overriding the given anim_state, as a string. This function requires either the PERMISSION_OVERRIDE_ANIMATIONS or PERMISSION_TRIGGER_ANIMATION runtime permission to be active.


## Arguments

| Name | Type | Description |
|---|---|---|
| `anim_state` | `string` | Animation state string to query. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `avatar_animation`, `permissions` |
