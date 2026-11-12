# `ll.ListSort`

```lua
ll.ListSort(src: {T}, stride: number, ascending: boolean | number) -> {T}
```

Creates a new list that is a sorted copy of the input list, organized in segments defined by the stride parameter, with elements ordered ascendingly when ascending is true or descendingly when false. This operation requires that the first element of each segment has the same data type.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `{T}` | List to be sorted. |
| `stride` | `number` | Number of entries per block/stride (defaults to 1 if less than 1). |
| `ascending` | `boolean | number` | Boolean. If TRUE, sorts in ascending order; if FALSE, sorts in descending order. |

**Returns:** `{T}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |
