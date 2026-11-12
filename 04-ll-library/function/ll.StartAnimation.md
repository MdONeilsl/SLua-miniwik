# `ll.StartAnimation`

```lua
ll.StartAnimation(anim: string) -> ()
```

Initiates the specified animation, either from the prim’s inventory or a built-in animation, on the avatar that granted the script the PERMISSION_TRIGGER_ANIMATION permission (which is automatically assigned when the script is attached to or sitting on an object).

## Arguments

| Name | Type | Description |
|---|---|---|
| `anim` | `string` | Name of the animation in the prim's inventory, or the built-in animation name. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `avatar_animation`, `permissions` |
