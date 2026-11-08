# `ll.ListSortStrided`

```lua
ll.ListSortStrided(src: {T}, stride: number, stride_index: number, ascending: boolean | number) -> {T}
```

Returns a copy of the input list, grouped into segments of size stride, and sorted within each segment based on the value at the specified stride_index position. Sorting follows ascending order when ascending is true, or descending when false.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `{T}` | List to be sorted. |
| `stride` | `number` | Number of entries per block/stride (defaults to 1 if less than 1). |
| `stride_index` | `number` | Zero-based index of the element within each stride to use as the sort key (negatives count backward from the end of the stride). |
| `ascending` | `boolean | number` | Boolean. If TRUE, sorts in ascending order; if FALSE, sorts in descending order. |

**Returns:** `{T}`

## Deprecated

- **use:** table.sort
- **reason:** Prefer structured tables over strided lists.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |