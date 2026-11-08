# `ll.MoveToTarget`

```lua
ll.MoveToTarget(target: vector, tau: number) -> ()
```

Applies critical damping to smoothly move a physical object to the specified target position within tau seconds. When tau is set to 0.0, damping is disabled; values above 0.2 are generally recommended for optimal performance.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `vector` | Target position vector in region coordinates. |
| `tau` | `number` | Timescale in seconds to critically damp the movement. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |