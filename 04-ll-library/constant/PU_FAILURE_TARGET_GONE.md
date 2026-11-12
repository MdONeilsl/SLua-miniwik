# `PU_FAILURE_TARGET_GONE`

This error code is returned during a path update if the intended `ll.Pursue` or `ll.Evade` target becomes untrackable, such as when the target exits the area or moves farther than approximately 30 meters beyond the designated region limits.

**Type:** `number`

**Value:** `0x05`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `CharacterPathUpdateType` |
