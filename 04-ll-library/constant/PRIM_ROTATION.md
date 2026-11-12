# `PRIM_ROTATION`

This prim parameter, designated as [PRIM_ROTATION, rotation global_rot], provides functionality to either retrieve or establish the overall rotational state of the prim. It serves a purpose analogous to calling `ll.GetRot`/`ll.SetRot`, however, developers should be aware that attempting to set this value on child prims may result in unexpected behavior.

**Type:** `number`

**Value:** `8`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimParam`, `PrimParamGet` |
