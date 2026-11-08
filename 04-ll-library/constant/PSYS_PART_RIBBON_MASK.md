# `PSYS_PART_RIBBON_MASK`

This particle flag merges emitted particles into a continuous ribbon structure. Textures automatically stretch to connect adjacent edges. The width is managed via the 'x' start/end scale, and the maximum visibility distance is dictated by 'y'. These ribbon segments are not oriented toward the camera; instead, they replicate the emitter's Z-axis direction and must undergo horizontal movement in order to be rendered.

**Type:** `number`

**Value:** `0x400`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ParticleFlag` |