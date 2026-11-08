# `ll.ListFindStrided`

```lua
ll.ListFindStrided(src: list, test: list, start_index: number, end_index: number, stride: number) -> number?
```

Finds the first occurrence of the specified list within the given strided segment of the source list, starting at the specified index and ending before the end index, advancing by the stride value. Returns -1 if no match is found.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `list` | List to search within. |
| `test` | `list` | List elements to search for. |
| `start_index` | `number` | Zero-based start index of the range to search. |
| `end_index` | `number` | Zero-based end index of the range to search. |
| `stride` | `number` | Number of entries per stride in the list. |

**Returns:** `number?`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `list` |