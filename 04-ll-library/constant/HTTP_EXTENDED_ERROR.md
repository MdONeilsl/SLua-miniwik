# `HTTP_EXTENDED_ERROR`

When `ll.HTTPRequest` is configured to TRUE, it ensures a key is always returned. Should any errors happen while processing the request, specific error details (provided in an RFC 7807 JSON format) will be communicated via the `http_response` event using this associated key.

**Type:** `number`

**Value:** `9`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `HTTPRequestParam` |