# `ll.ListInsertList`

```lua
ll.ListInsertList(dest: {T}, src: {T}, start: number) -> {T}
```

Creates a new list that combines all elements from dest, with the elements of src inserted at the specified zero-based index position, leaving the original dest list unchanged.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dest` | `{T}` | Target destination list. |
| `src` | `{T}` | Source list to insert. |
| `start` | `number` | Zero-based index where insertion begins. |

**Returns:** `{T}`

## Deprecated

- **use:** table.insert
- **reason:** Unnecessary table copying. Fastcall.

## Definition fields

| Field | Value |
|---|---|
energy | 10.0 |
sleep | 0.0 |
categories | list |
