# `ll.WanderWithin`

```lua
ll.WanderWithin(origin: vector, dist: vector, options: list) -> ()
```

Causes a pathfinding character to roam freely around a specified central point, confined within a bounding box defined by the distance vector and adjusted via the provided options.

## Arguments

| Name | Type | Description |
|---|---|---|
| `origin` | `vector` | Center coordinate position vector to wander about. |
| `dist` | `vector` | A vector specifying the maximum distance limits (half-extents) along each world-aligned axis from the origin. |
| `options` | `list` | A list of WANDER_* flags and parameters to configure the wander behavior. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |