# `PRIM_COLOR`

This Prim parameter is used to obtain or assign the Blinn-Phong color and associated opacity value for a face.

integer face – specifies either the individual face number or ALL_SIDES.
vector color – defines the RGB color using <R, G, B> components (<0.0, 0.0, 0.0> represents black, while <1.0, 1.0, 1.0> stands for white).
float alpha – dictates opacity, ranging from 0.0 (indicating clear) up to 1.0 (indicating solid) (must satisfy the constraint 0.0 <= alpha <= 1.0).

**Type:** `number`

**Value:** `18`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimParam`, `PrimParamGet` |
