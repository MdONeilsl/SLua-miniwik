# `HTTP_BODY_MAXLENGTH`

Configures the upper limit for the size, measured in UTF-8 encoded bytes, of an HTTP response payload. This ceiling is contingent upon which VM environment is operational (specifically, Mono limits to 16384 bytes, while LSO allows up to 4096 bytes).

**Type:** `number`

**Value:** `2`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `HTTPRequestParam` |
