# `ll.DetectedTouchST`

```lua
ll.DetectedTouchST(index: number) -> vector
```

When a prim is touched, this function returns the surface coordinates in the form (<s, t, 0.0>), where s and t represent the horizontal and vertical positions on the prim’s surface, usually ranging from 0.0 to 1.0. If the coordinates cannot be resolved, it returns TOUCH_INVALID_TEXCOORD.

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
