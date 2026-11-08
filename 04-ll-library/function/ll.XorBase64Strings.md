# `ll.XorBase64Strings`

```lua
ll.XorBase64Strings(str1: string, str2: string) -> string
```

This function is deprecated and should be replaced with ll.XorBase64 for correct behavior. It remains for backward compatibility but incorrectly applies a bitwise XOR operation to the two provided Base64 strings.

## Arguments

| Name | Type | Description |
|---|---|---|
| `str1` | `string` | First Base64 string. |
| `str2` | `string` | Second Base64 string (will repeat if shorter than str1). |

**Returns:** `string`

## Deprecated

- **use:** ll.XorBase64

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.3` |
| `categories` | `data_conversion` |