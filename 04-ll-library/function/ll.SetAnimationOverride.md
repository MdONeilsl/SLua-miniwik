# `ll.SetAnimationOverride`

```lua
ll.SetAnimationOverride(anim_state: string, anim: string) -> ()
```

Sets a custom animation to replace the default for the specified animation state, where the animation must either be present in the object’s inventory or be a built-in animation name. This operation requires the PERMISSION_OVERRIDE_ANIMATIONS permission.


## Arguments

| Name | Type | Description |
|---|---|---|
| `anim_state` | `string` | Animation state to override. |
| `anim` | `string` | Name of an animation in the prim's inventory, or a built-in animation name. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_animation`, `permissions` |
