# `STATUS_DIE_AT_EDGE`

This status flag, which defaults to TRUE, dictates that if an object moves outside of the world boundaries—a scenario useful for items such as rockets or bullets—the object will be deleted rather than being returned. Be aware that this setting can be overridden by STATUS_RETURN_AT_EDGE.

**Type:** `number`

**Value:** `0x80`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectStatusParam` |