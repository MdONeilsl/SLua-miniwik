# `ll.TargetOmega`

```lua
ll.TargetOmega(axis: vector, spinrate: number, gain: number) -> ()
```

Enables a client-side rotational effect around the local axis, with angular velocity determined by multiplying spinrate by the axis vector’s magnitude (in radians per second), and strength controlled by the gain parameter. Setting spinrate to 0.0 disables the rotation.


## Arguments

| Name | Type | Description |
|---|---|---|
| `axis` | `vector` | Local axis vector around which the object rotates. |
| `spinrate` | `number` | Rotation rate multiplier in radians per second. |
| `gain` | `number` | A float modulating the rotational strength (disables the rotation if set to 0.0). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |