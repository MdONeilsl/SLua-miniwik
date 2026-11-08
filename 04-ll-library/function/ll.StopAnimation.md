# `ll.StopAnimation`

```lua
ll.StopAnimation(anim: string | uuid) -> ()
```

Halts the given animation — specified by its name from the prim’s inventory, its UUID, or a built-in animation identifier — on the avatar that granted the script the PERMISSION_TRIGGER_ANIMATION permission (which is automatically assigned when the script is attached to or sitting on an object).


## Arguments

| Name | Type | Description |
|---|---|---|
| `anim` | `string | uuid` | Name of the animation in the prim's inventory, the UUID of the animation, or the built-in animation name. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `avatar_animation`, `permissions` |