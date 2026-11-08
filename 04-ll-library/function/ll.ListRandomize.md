# `ll.ListRandomize`

```lua
ll.ListRandomize(src: {T}, stride: number) -> {T}
```

Produces a new list that is a shuffled version of the input list `src`, grouped into segments of length `stride`. If the total number of elements in `src` is not evenly divisible by `stride`, the function does not perform any randomization.

## Arguments

| Name | Type | Description |
|---|---|---|
| src | {T} | Source list to randomize. |
| stride | number | Size of each randomized block (defaults to 1 if less than 1). |

**Returns:** `{T}`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `list` |