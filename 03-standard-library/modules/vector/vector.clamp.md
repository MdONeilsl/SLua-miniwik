# `vector.clamp`

```lua
vector.clamp(vec: vector, min: vector, max: vector) -> vector
```

Limits each component of the input vector to lie within the specified minimum and maximum bounds.

## Arguments

| Name | Type | Description |
|---|---|---|
| `vec` | `vector` | Input vector whose components are to be constrained. |
| `min` | `vector` | Lower bound for each component’s value. |
| `max` | `vector` | Upper bound for each component’s value. |

**Returns:** `vector`