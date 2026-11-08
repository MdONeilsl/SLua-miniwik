# `PRIM_MEDIA_WHITELIST`

Retrieves and modifies the media whitelist, which must be provided as an array of URL strings (limited to 64 URLs or 1024 characters, whichever constraint is met first). When using SLua, pass a {string} array; this input will then be serialized into an escaped, comma-separated string format required by the underlying LSL API.

**Type:** `number`

**Value:** `12`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimMediaParam` |