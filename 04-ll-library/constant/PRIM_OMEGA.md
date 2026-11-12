# `PRIM_OMEGA`

This prim parameter provides functionality to retrieve, modify, or turn off a physically simulated client-side rotation (similar in function to `ll.TargetOmega`). The required parameters are: `vector axis` specifies the arbitrary direction around which the object will spin; `float spinrate` determines the rotational speed measured in radians per second; and `float gain` acts as a multiplier for the final spinrate, stopping the rotation entirely if set to zero.

**Type:** `number`

**Value:** `32`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimParam`, `PrimParamGet` |
