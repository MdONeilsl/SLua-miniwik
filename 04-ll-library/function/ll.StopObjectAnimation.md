# `ll.StopObjectAnimation`

```lua
ll.StopObjectAnimation(anim: string | uuid) -> ()
```

Halts the given animation, identified by its name from the prim's inventory, its UUID, or a built-in animation identifier, on the rigged mesh object linked to the current script.

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
| `categories` | `object_animation` |