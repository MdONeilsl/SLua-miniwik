# `PSYS_PART_TARGET_LINEAR_MASK`

This particle flag dictates that emitted particles will follow a straight path at consistent intervals toward the location specified by PSYS_SRC_TARGET_KEY. This effect disregards influence from non-DROP patterns, radius, burst speeds, angles, omega, acceleration, and wind. When used in conjunction with bounce while the target is positioned beneath the emitter, it results in an upward deflection of particles.

**Type:** `number`

**Value:** `0x80`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ParticleFlag` |
