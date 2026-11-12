# `ll.IntegerToBase64`

```lua
ll.IntegerToBase64(number: number) -> string
```

Converts the given integer into an 8-character Base64 string, encoding it in big-endian format.


## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | `number` | Integer number to encode. |

**Returns:** `string`

## Deprecated

- **reason:** Use 'llbase64.encode' and 'string.pack' or 'buffer.writei32' instead.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion` |
