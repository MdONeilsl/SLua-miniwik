# `PRIM_GLTF_ALPHA_MODE_BLEND`

This setting dictates the alpha rendering method for PRIM_GLTF_BASE_COLOR within GLTF. It processes materials that exhibit transparency (using alpha blending) within a linear color space. The material's opacity multiplier is applied by multiplying it against the texture's inherent transparency value. Be aware that this mode may encounter issues related to depth sorting and performance efficiency.

**Type:** `number`

**Value:** `1`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `GLTFAlphaMode` |