# `HTTP_CUSTOM_HEADER`

This allows adding custom HTTP headers when making a request (a maximum of 8 headers can be supplied). When using SLua, you must provide a string-keyed table where keys are header names and values are their corresponding values; consequently, the serializer will generate one HTTP_CUSTOM_HEADER/key/value set for every item entered. Please note that certain default or sensitive headers are restricted for security purposes.

**Type:** `number`

**Value:** `5`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `HTTPRequestParam` |
