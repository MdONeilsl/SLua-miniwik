# `ll.ApplyImpulse`

```lua
ll.ApplyImpulse(momentum: vector, is_local: boolean | number) -> ()
```

This function adds a linear impulse, represented as a momentum vector, to a physical entity. When `is_local` is set to TRUE, the impulse is interpreted in the object’s local coordinate system; if FALSE, it is applied using the global region coordinate system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `momentum` | `vector` | Linear impulse vector to apply. |
| `is_local` | `boolean | number` | Boolean. If TRUE, momentum is treated as a local directional vector; if FALSE, it is treated as a global region vector. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |