# `ll.Base64ToInteger`

```lua
ll.Base64ToInteger(str: string) -> number
```

Decodes the provided Base64 string into a big-endian integer value. If the input string exceeds 8 characters, it returns zero; if it contains fewer than 6 characters, the result is undefined.

## Arguments

| Name | Type | Description |
|---|---|---|
| `str` | `string` | Base64-encoded string to decode. |

**Returns:** `number`

## Deprecated

- **reason:** Use 'llbase64.decode' and 'string.unpack' or 'buffer.readi32' instead.

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion` |
