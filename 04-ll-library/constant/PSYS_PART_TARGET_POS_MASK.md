# `PSYS_PART_TARGET_POS_MASK`

This particle flag dictates that emitted particles will adjust their trajectory to move toward the target defined by `PSYS_SRC_TARGET_KEY` throughout their existence. Should there be no designated or accessible target, the particles will instead aim for the prim from which they originated.

**Type:** `number`

**Value:** `0x40`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ParticleFlag` |