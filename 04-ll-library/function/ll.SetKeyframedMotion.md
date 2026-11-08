# `ll.SetKeyframedMotion`

```lua
ll.SetKeyframedMotion(keyframes: list, options: list) -> ()
```

Moves a non-physical object along a path defined by position, orientation, and time data in the keyframes list, with behavior controlled by the options. Collisions with keyframed objects are not considered. Providing an empty keyframes list stops the motion.

## Arguments

| Name | Type | Description |
|---|---|---|
| `keyframes` | `list` | A strided list of the form [vector position, rotation orientation, float time] representing sequential relative keyframes (minimum time is 1/9s). |
| `options` | `list` | A list of options (KFM_* constants) to modify playback behavior. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |