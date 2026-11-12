# `ll.DetectedTouchPos`

```lua
ll.DetectedTouchPos(index: number) -> vector
```

Provides the vector position of where the object was touched, using the specified index, expressed in region coordinates unless the object is a HUD, in which case it returns screen-space coordinates.


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
