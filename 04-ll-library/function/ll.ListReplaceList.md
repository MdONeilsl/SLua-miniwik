# `ll.ListReplaceList`

```lua
ll.ListReplaceList(dest: {T}, src: {T}, start_index: number, end_index: number) -> {T}
```

Creates a new list by replacing the elements in dest from start_index to end_index (inclusive) with the elements from src, maintaining the original list's structure outside the replaced range.

## Arguments

| Name | Type | Description |
|---|---|---|
| dest | {T} | Target destination list. |
| src | {T} | Source list to insert. |
| start_index | number | Zero-based start index (inclusive) of the replaced range. |
| end_index | number | Zero-based end index (inclusive) of the replaced range. |

**Returns:** `{T}`

## Deprecated

- **use:** t[n] = x
- **reason:** Unnecessary table copying.

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | list |