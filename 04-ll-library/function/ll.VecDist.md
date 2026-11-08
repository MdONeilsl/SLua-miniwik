# `ll.VecDist`

```lua
ll.VecDist(vec_a: vector, vec_b: vector) -> number
```

Computes and returns a non-negative scalar value indicating the straight-line distance between two given vectors.


## Arguments

| Name | Type | Description |
|---|---|---|
| `vec_a` | `vector` | First vector. |
| `vec_b` | `vector` | Second vector. |

**Returns:** `number`

## Deprecated

- **use:** vector.magnitude
- **reason:** It's a fastcall.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `vector` |