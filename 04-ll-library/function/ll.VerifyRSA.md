# `ll.VerifyRSA`

```lua
ll.VerifyRSA(public_key: string, msg: string, signature: string, algorithm: string) -> boolean
```

Returns 1 if the provided Base64-encoded signature is confirmed valid for the given message using the specified digest algorithm and public key; returns 0 if verification fails.


## Arguments

| Name | Type | Description |
|---|---|---|
| `public_key` | `string` | PEM-formatted public key to use for signature verification. |
| `msg` | `string` | Message string that was signed. |
| `signature` | `string` | Base64-encoded signature to verify. |
| `algorithm` | `string` | Cryptographic digest algorithm to use. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `cryptography` |
