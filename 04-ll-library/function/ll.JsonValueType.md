# `ll.JsonValueType`

```lua
ll.JsonValueType(json: string, specifiers: list) -> string
```

Takes a JSON string and a path specification to extract the type of the value at that location, returning the corresponding JSON type constant (e.g., JSON_OBJECT, JSON_NUMBER).

## Arguments

| Name | Type | Description |
|---|---|---|
| `json` | `string` | JSON string containing the value to query. |
| `specifiers` | `list` | A list of key names or array indices specifying the path to the value. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion`, `json` |