# `STATUS_ROTATE_Y`

This status flag (which defaults to TRUE) determines if physical spinning is permitted along the object's intrinsic Y-axis. If this flag is set to FALSE, rotation about the local Y-axis will be blocked. As an illustration, consider a sit-and-spin device: it spins around the Z axis (vertical) but cannot rotate on the X or Y axes.

**Type:** `number`

**Value:** `0x4`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectStatusParam` |
