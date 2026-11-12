# `ll.DetectedKey`

```lua
ll.DetectedKey(number: number) -> uuid
```

Given a detection index, this function retrieves the UUID of the corresponding detected object or avatar; it returns NULL_KEY if the index is invalid.


## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | `number` | Index of the detection information. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected`, `uuid` |
