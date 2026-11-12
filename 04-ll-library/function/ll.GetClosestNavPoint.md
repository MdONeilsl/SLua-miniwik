# `ll.GetClosestNavPoint`

```lua
ll.GetClosestNavPoint(point: vector, options: list) -> {vector}
```

Finds the nearest point on the navigation mesh relative to the given position, which is specified in region-local coordinates; returns an empty list if no valid point is located. The behavior can be customized via the options parameter.

## Arguments

| Name | Type | Description |
|---|---|---|
| point | vector | Position vector in region-local coordinates. |
| options | list | A list of GCNP_* flags and parameters to configure the search limits. |

**Returns:** `{vector}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |
