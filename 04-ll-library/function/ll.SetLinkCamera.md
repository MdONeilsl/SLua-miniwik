# `ll.SetLinkCamera`

```lua
ll.SetLinkCamera(link: number, eye: vector, at: vector) -> ()
```

Configures the camera's eye and target positions relative to the specified linked prim, affecting avatars seated on it.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `eye` | `vector` | Eye offset position vector in local coordinates relative to the prim. |
| `at` | `vector` | Look-at offset position vector in local coordinates relative to the prim. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `camera`, `sit` |
