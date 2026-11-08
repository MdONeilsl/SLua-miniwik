# `STATUS_DIE_AT_NO_ENTRY`

This status flag, which has a default value of FALSE, ensures the object is deleted should it try to enter an unauthorized or fully occupied parcel. However, objects configured as no-copy disregard this setting and will remain physically present in the world environment.

**Type:** `number`

**Value:** `0x800`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectStatusParam` |