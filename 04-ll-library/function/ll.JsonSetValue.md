# `ll.JsonSetValue`

```lua
ll.JsonSetValue(json: string, specifiers: list, value: string) -> string
```

This function generates a new JSON string where the element at the path specified by specifiers is replaced with the given value. It accepts JSON_APPEND to add items to arrays, and JSON_DELETE to remove the targeted element. If the operation attempts to write beyond array bounds or uses array indices at non-array levels, it returns JSON_INVALID.

## Arguments

| Name | Type | Description |
|---|---|---|
| `json` | `string` | Source JSON string to modify. |
| `specifiers` | `list` | A list of key names or array indices specifying the path to add, update, or delete. |
| `value` | `string` | New value to set, or the JSON_DELETE constant to delete the targeted element. |

**Returns:** `string`

## Deprecated

- **use:** lljson.encode
- **reason:** Also, the indices are zero-based.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion`, `json` |
