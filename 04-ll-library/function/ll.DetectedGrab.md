# `ll.DetectedGrab`

```lua
ll.DetectedGrab(number: number) -> vector
```

This function provides the positional offset at which a user is grasping the object, applicable exclusively during touch interactions; if the provided index is invalid, it returns the zero vector <0.0, 0.0, 0.0>.


## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | `number` | Index of the detection information. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected`, `touch` |
