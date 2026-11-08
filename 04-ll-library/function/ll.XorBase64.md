# `ll.XorBase64`

```lua
ll.XorBase64(str1: string, str2: string) -> string
```

Applies a bitwise XOR operation to two Base64-encoded strings, returning the result as a Base64 string. If str2 is shorter than str1, it is repeated to match the length of str1.


## Arguments

| Name | Type | Description |
|---|---|---|
| `str1` | `string` | First Base64 string. |
| `str2` | `string` | Second Base64 string (will repeat if shorter than str1). |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion` |