# `ll.JsonGetValue`

```lua
ll.JsonGetValue(json: string, specifiers: list) -> string
```

Extracts a value from the provided JSON string by following a hierarchical path defined by the specifiers, and returns it as a string.


## Arguments

| Name | Type | Description |
|---|---|---|
| `json` | `string` | JSON string to query. |
| `specifiers` | `list` | A list of key names or array indices specifying the path to the desired value. |

**Returns:** `string`

## Deprecated

- **use:** lljson.decode
- **reason:** Also, the indices are zero-based.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion`, `json` |
