# `ll.List2List`

```lua
ll.List2List(src: {T}, start_index: number, end_index: number) -> {T}
```

Creates a new list by extracting elements from the source list between the specified start and end indices, inclusive. Negative indices are interpreted as offsets from the end of the list.

## Arguments

| Name | Type | Description |
|---|---|---|
| src | {T} | Source list to slice. |
| start_index | number | Zero-based start index (inclusive). |
| end_index | number | Zero-based end index (inclusive). |

**Returns:** `{T}`

## Deprecated

- **reason:** Use 'unpack' (fastcall) or 'table.move' instead. Prefer structured tables over strided lists.

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `list` |