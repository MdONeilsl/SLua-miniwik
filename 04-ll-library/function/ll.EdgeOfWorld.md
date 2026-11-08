# `ll.EdgeOfWorld`

```lua
ll.EdgeOfWorld(pos: vector, dir: vector) -> boolean
```

Determines whether the ray cast from position `pos` in the direction of `dir` encounters the edge of the world—meaning there is no adjacent simulator present. Returns 1 (true) if the ray hits the world boundary, or 0 (false) if it encounters a neighboring simulator.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates. |
| `dir` | `vector` | Direction vector. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `region` |