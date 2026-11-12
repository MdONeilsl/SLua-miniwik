# `ll.List2ListSlice`

```lua
ll.List2ListSlice(src: {T}, start_index: number, end_index: number, stride: number, slice_index: number) -> {T}
```

Extracts the slice_index'th element from each stride within the specified inclusive range [start_index, end_index] in the strided list src. The stride value must be a positive integer.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | {T} | Source strided list. |
| `start_index` | number | Zero-based start index (inclusive). |
| `end_index` | number | Zero-based end index (inclusive). |
| `stride` | number | Number of entries per stride (defaults to 1 if less than 1). |
| `slice_index` | number | Zero-based element index within each stride to extract (negatives count backward from the end of the stride). |

**Returns:** `{T}`

## Deprecated

- **reason:** Prefer structured tables over strided lists.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |
