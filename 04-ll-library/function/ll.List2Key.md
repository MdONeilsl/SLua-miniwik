# `ll.List2Key`

```lua
ll.List2Key(src: list, index: number) -> uuid
```

Retrieves the UUID key at the specified zero-based index from the given list. If the index is invalid or the value cannot be converted to a key, it returns the null key string.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `list` | Source list containing the element of interest. |
| `index` | `number` | Zero-based index of the entry. |

**Returns:** `uuid`

## Deprecated

- **reason:** Use '[]' and 'touuid' instead.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion`, `list` |