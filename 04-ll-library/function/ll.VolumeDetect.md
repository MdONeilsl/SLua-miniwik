# `ll.VolumeDetect`

```lua
ll.VolumeDetect(detect: boolean | number) -> ()
```

When detect is set to TRUE, VolumeDetect is activated, causing the object to behave as a phantom and allowing physical objects and avatars to pass through it. It initiates collision_start upon first contact and collision_end when the intersection ceases, while standard collision events are disabled during the overlap.


## Arguments

| Name | Type | Description |
|---|---|---|
| `detect` | `boolean | number` | Boolean. If TRUE, enables VolumeDetect; if FALSE (default), disables it. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `sensor` |