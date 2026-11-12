# `PASS_NEVER`

This constant must be supplied when calling event-passing functions; it guarantees that any events originating in a child prim will not propagate up to the root prim, even if those events are processed by local child script handlers.

**Type:** `number`

**Value:** `2`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PassMode` |
