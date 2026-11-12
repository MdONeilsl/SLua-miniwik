# `ll.ListFindList`

```lua
ll.ListFindList(src: list, test: list) -> number?
```

Finds the first occurrence of the specified list `test` inside `src` and returns its zero-based index; returns -1 if the sublist is not present.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `list` | List to search within. |
| `test` | `list` | List elements to search for. |

**Returns:** `number?`

## Deprecated

- **use:** table.find
- **reason:** Prefer dictionaries or single-item searches.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |
