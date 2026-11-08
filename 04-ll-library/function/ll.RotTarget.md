# `ll.RotTarget`

```lua
ll.RotTarget(rot: quaternion, error: number) -> number
```

Sets the specified rotation as a target with a tolerance angle in radians, firing events when the target is reached or not reached. Provides an integer handle for removing the target using ll.RotTargetRemove.

## Arguments

| Name | Type | Description |
|---|---|---|
| `rot` | `quaternion` | Target rotation to track. |
| `error` | `number` | Tolerance angle in radians defining when the target rotation is considered reached. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |