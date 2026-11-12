# `ll.VecNorm`

```lua
ll.VecNorm(vec: vector) -> vector
```

Computes a unit vector in the same direction as the input vector; if the input is <0, 0, 0>, it returns <0, 0, 0>.


## Arguments

| Name | Type | Description |
|---|---|---|
| `vec` | `vector` | Vector to normalize. |

**Returns:** `vector`

## Deprecated

- **use:** vector.normalize
- **reason:** It's a fastcall.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `vector` |
