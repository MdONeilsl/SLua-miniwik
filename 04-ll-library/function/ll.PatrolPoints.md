# `ll.PatrolPoints`

```lua
ll.PatrolPoints(patrolPoints: {vector}, options: list) -> ()
```

Causes a pathfinding character to move in sequence across the positions listed in patrolPoints, with behavior modifiable via the options parameter.

## Arguments

| Name | Type | Description |
|---|---|---|
| `patrolPoints` | `{vector}` | A list of at least two position vectors representing the patrol path. |
| `options` | `list` | A list of PATROL_* flags and parameters to configure the patrol behavior. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |
