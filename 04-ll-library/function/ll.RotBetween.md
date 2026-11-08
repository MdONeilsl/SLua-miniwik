# `ll.RotBetween`

```lua
ll.RotBetween(start_vec: vector, end_vec: vector) -> quaternion
```

Computes the quaternion representing the minimal rotation required to align start_vec with end_vec.


## Arguments

| Name | Type | Description |
|---|---|---|
| `start_vec` | `vector` | Starting vector. |
| `end_vec` | `vector` | Ending vector. |

**Returns:** `quaternion`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math`, `math_3d`, `math_trig`, `quaternion` |