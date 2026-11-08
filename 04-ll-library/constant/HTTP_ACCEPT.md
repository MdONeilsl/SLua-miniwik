# `HTTP_ACCEPT`

When utilizing ll.HTTPRequest, this parameter allows developers to replace the standard Accept HTTP header by specifying desired custom MIME types, for example, application/json or text/html. If a response contains a content type that was not listed in the provided types, the system will return an HTTP status code of 415.

**Type:** `number`

**Value:** `8`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `HTTPRequestParam` |