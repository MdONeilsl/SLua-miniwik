# `RC_DETECT_PHANTOM`

This flag operates with ll.CastRay. When given a TRUE or non-zero value, it enables detection of both phantom and volume-detect objects; these object types cannot be filtered separately. Consequently, this setting supersedes any configurations defined by RC_REJECT_NONPHYSICAL and RC_REJECT_PHYSICAL within RC_REJECT_TYPES.

**Type:** `number`

**Value:** `1`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `RayCastParam` |