# `PRIM_REFLECTION_PROBE_MIRROR`

This flag option must be used alongside PRIM_REFLECTION_PROBE. Enabling it causes low-roughness PBR materials that are intersected to behave like mirrors. Be aware that these mirrors will not reflect avatars unless you have also enabled PRIM_REFLECTION_PROBE_DYNAMIC, and using this feature incurs a performance overhead.

**Type:** `number`

**Value:** `4`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ReflectionProbeType` |
