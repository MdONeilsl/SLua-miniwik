# `ll.DetectedTouchNormal`

```lua
ll.DetectedTouchNormal(index: number) -> vector
```

Given a touch detection index, this function retrieves the surface normal vector at that point, which is orthogonal to the surface. It complements ll.DetectedTouchBinormal for computing the tangent space.


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
