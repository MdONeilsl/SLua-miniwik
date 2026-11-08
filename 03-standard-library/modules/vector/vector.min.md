# `vector.min`

```lua
vector.min(vec: vector, ...) -> vector
```

Computes the component-wise minimum across all provided vectors, using `math.min` on each corresponding element.

## Arguments

| Name | Type | Description |
|---|---|---|
| `vec` | `vector` | First vector to include in the minimum calculation. |
| `...` | `...vector` | Additional vectors to include in the minimum calculation. |

**Returns:** `vector`