# `ll.MD5String`

```lua
ll.MD5String(src: string, nonce: number) -> string
```

Produces a 32-character hexadecimal string that is the MD5 hash of the input string, with the nonce appended as a colon-prefixed value.


## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Source string to hash. |
| `nonce` | `number` | Nonce string used as a salt. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `cryptography` |