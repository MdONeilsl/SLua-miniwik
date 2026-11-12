# `vector.max`

```lua
vector.max(vec: vector, ...) -> vector
```

Applies the maximum operation component-wise across all input vectors, returning a new vector with the highest value in each dimension.

## Arguments

| Name | Type | Description |
|---|---|---|
| `vec` | `vector` | Primary vector to include in the maximum calculation. |
| `...` | `...vector` | Additional vectors to compare against for component-wise maximum. |

**Returns:** `vector`
