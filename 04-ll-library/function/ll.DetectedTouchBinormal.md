# `ll.DetectedTouchBinormal`

```lua
ll.DetectedTouchBinormal(index: number) -> vector
```

At the specified touch index, this function retrieves the surface binormal vector—aligned with the positive T (V) axis of tangent space—and is typically paired with ll.DetectedTouchNormal to establish tangent space orientation.


## Arguments

| Name | Type | Description |
|---|---|---|
| `index` | number | Index of the detection information. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected`, `touch` |
