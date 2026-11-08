# `vector.normalize`

```lua
vector.normalize(vec: vector) -> vector
```

Computes a unit vector in the same direction as the input, scaling it to length one; returns <NaN, NaN, NaN> if the input is zero.

## Arguments

| Name | Type | Description |
|---|---|---|
| `vec` | `vector` | Input vector to scale to unit length. |

**Returns:** `vector`