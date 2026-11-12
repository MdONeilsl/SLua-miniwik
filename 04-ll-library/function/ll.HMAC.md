# `ll.HMAC`

```lua
ll.HMAC(private_key: string, msg: string, algorithm: string) -> string
```

Generates a Base64-encoded HMAC signature for the given message string, using the provided secret key and the specified cryptographic hash algorithm from the set: md5, sha1, sha224, sha256, sha384, or sha512.

## Arguments

| Name | Type | Description |
|---|---|---|
| `private_key` | `string` | PEM-formatted secret key to use for the HMAC hash. |
| `msg` | `string` | Message string to be hashed. |
| `algorithm` | `string` | Cryptographic digest algorithm to use. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `cryptography` |
