# `PRIM_POINT_LIGHT`

A parameter that allows for configuring local light sources. Color values must be provided in linear space; if you are converting from sRGB, use llsRGB2Linear. The boolean field controls activation (TRUE enables, FALSE disables). The `linear_color` vector specifies the RGB color component (<R, G, B&>), where <0.0, 0.0, 0.0> represents black and <1.0, 1.0, 1.0> represents white. The `intensity` float dictates a range between 0.0 and 1.0. The `radius` float operates within the boundaries of 0.1 to 20.0. Finally, the `falloff` float must be set between 0.01 and 2.0.

**Type:** `number`

**Value:** `23`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimParam`, `PrimParamGet` |
