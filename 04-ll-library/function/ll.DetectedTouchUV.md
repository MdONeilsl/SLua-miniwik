# `ll.DetectedTouchUV`

```lua
ll.DetectedTouchUV(index: number) -> vector
```

Given an index, this function returns the UV texture coordinates (<u, v, 0.0>) at the point where the prim was touched. The X and Y components represent the horizontal and vertical texture coordinates, respectively, usually ranging from [0.0, 1.0], though this may vary based on texture repeats or rotation. If the coordinates cannot be determined, the function returns TOUCH_INVALID_TEXCOORD.

## Arguments

| Name | Type | Description |
|---|---|---|
| `index` | `number` | Index of the detection information. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected`, `touch` |
