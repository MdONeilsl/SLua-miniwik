# `ll.XorBase64StringsCorrect`

```lua
ll.XorBase64StringsCorrect(str1: string, str2: string) -> string
```

This function is deprecated; use ll.XorBase64 instead. It executes a bitwise XOR operation on two Base64-encoded strings, str1 and str2, provided neither contains null characters.

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
| `sleep` | `0.0` |
| `categories` | `data_conversion` |
