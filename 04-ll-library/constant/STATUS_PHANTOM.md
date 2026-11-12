# `STATUS_PHANTOM`

This status flag defaults to FALSE, but when enabled (set to TRUE), it renders the entire object non-colliding or 'phantom,' thus permitting avatars and other objects to pass right through it. Developers should consider utilizing this setting for any object that rotates or moves but does not need physical interaction. Furthermore, it proves beneficial when implementing volumetric lighting simulations.

**Type:** `number`

**Value:** `0x10`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectStatusParam` |
