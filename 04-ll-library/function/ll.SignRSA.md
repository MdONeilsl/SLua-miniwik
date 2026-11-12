# `ll.SignRSA`

```lua
ll.SignRSA(private_key: string, msg: string, algorithm: string) -> string
```

Generates a Base64-encoded RSA signature for the given message, utilizing the provided PEM-encoded private key and the selected hash algorithm (sha1, sha224, sha256, sha384, or sha512). This function is intended to work in conjunction with ll.VerifyRSA to enable message authentication.

## Arguments

| Name | Type | Description |
|---|---|---|
| `private_key` | `string` | PEM-formatted private key. |
| `msg` | `string` | Message contents to sign. |
| `algorithm` | `string` | Digest algorithm to use (sha1, sha224, sha256, sha384, or sha512). |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `cryptography` |
