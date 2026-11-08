# `ll.DetectedPos`

```lua
ll.DetectedPos(number: number) -> vector
```

Given a detection index, this function retrieves the position vector of the corresponding detected object or avatar in region coordinates; if the index is invalid, it returns <0.0, 0.0, 0.0>.

## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | number | Index of the detection information. |

**Returns:** `vector`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected` |