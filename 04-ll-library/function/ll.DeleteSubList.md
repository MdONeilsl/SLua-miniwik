# `ll.DeleteSubList`

```lua
ll.DeleteSubList(src: {T}, start_index: number, end_index: number) -> {T}
```

Returns a new list that is a copy of src with the elements from start_index through end_index (inclusive) deleted. Negative indices are interpreted as offsets from the end of the list. When start_index exceeds end_index, no elements are removed from that range.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `{T}` | Source list to copy and modify. |
| `start_index` | `number` | Starting index of the slice to remove (inclusive). |
| `end_index` | `number` | Ending index of the slice to remove (inclusive). |

**Returns:** `{T}`

## Deprecated

- **use:** table.remove
- **reason:** Unnecessary table copying.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |