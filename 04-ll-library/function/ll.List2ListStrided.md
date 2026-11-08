# `ll.List2ListStrided`

```lua
ll.List2ListStrided(src: {T}, start_index: number, end_index: number, stride: number) -> {T}
```

Creates a new list by extracting the first element from each stride of the input strided list, limited to the range defined by the inclusive start and end indices.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `{T}` | Source strided list. |
| `start_index` | number | Zero-based start index (inclusive). |
| `end_index` | number | Zero-based end index (inclusive). |
| `stride` | number | Number of entries per stride (defaults to 1 if less than 1). |

**Returns:** `{T}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |