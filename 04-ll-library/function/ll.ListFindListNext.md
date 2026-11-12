# `ll.ListFindListNext`

```lua
ll.ListFindListNext(src: list, test: list, instance: number) -> number?
```

Returns the zero-based index of the nth occurrence of the specified list within the source list; returns -1 if the specified instance is not present.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `list` | List to search within. |
| `test` | `list` | List elements to search for. |
| `instance` | `number` | Zero-based occurrence index of the match to find. |

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
