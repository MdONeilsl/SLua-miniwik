# `ll.GetStaticPath`

```lua
ll.GetStaticPath(start_pos: vector, end_pos: vector, radius: number, params: list) -> {any}
```

Generates a sequence of position vectors that define waypoints for navigating from a start point to an end point using the static navigation mesh, tailored to a character with the given radius. This function disregards movable obstacles and operates across any region, irrespective of the current dynamic pathfinding state.


## Arguments

| Name | Type | Description |
|---|---|---|
| `start_pos` | `vector` | Starting position vector. |
| `end_pos` | `vector` | Target end position vector. |
| `radius` | `number` | Radius of the character path, between 0.125m and 5.0m. |
| `params` | `list` | A list specifying the CHARACTER_TYPE parameter (defaults to CHARACTER_TYPE_NONE). |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |
