# `ll.Base64ToString`

```lua
ll.Base64ToString(str: string) -> string
```

Converts a Base64-encoded string into a standard string by treating the decoded byte sequence as UTF-8, replacing any unprintable characters with question marks.

## Arguments

| Name | Type | Description |
|---|---|---|
| `str` | `string` | Base64-encoded string to decode. |

**Returns:** `string`

## Deprecated

- **use:** llbase64.decode
- **reason:** 

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion` |
