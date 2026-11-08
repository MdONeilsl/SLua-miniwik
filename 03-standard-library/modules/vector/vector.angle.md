# `vector.angle`

```lua
vector.angle(start_vec: vector, end_vec: vector, axis: vector?) -> number
```

Computes the angular difference in radians between start_vec and end_vec, with optional axis to define rotational direction; if omitted, defaults to cross product of start_vec and end_vec.

## Arguments

| Name | Type | Description |
|---|---|---|
| `start_vec` | `vector` | Initial vector defining the starting point of the angle. |
| `end_vec` | `vector` | Final vector defining the endpoint of the angle. |
| `axis` | `vector?` | Optional reference vector to assign a signed orientation to the angle. |

**Returns:** `number`