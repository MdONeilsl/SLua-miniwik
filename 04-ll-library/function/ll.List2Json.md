# `ll.List2Json`

```lua
ll.List2Json(type: string, values: list) -> string
```

Transforms the provided list into a JSON-formatted string, specifying whether it should be an array or object. If serialization fails, it returns JSON_INVALID.


## Arguments

| Name | Type | Description |
|---|---|---|
| type | `string` | |
| values | `list` | List of values to serialize. |

**Returns:** `string`

## Deprecated

- **use:** lljson.encode

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion`, `json`, `list` |
