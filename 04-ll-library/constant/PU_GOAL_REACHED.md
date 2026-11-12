# `PU_GOAL_REACHED`

This status code for path updates is emitted when the character successfully arrives at its target destination, leading it to either halt movement or select an alternative objective (in the case of autonomous wandering).

**Type:** `number`

**Value:** `0x01`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `CharacterPathUpdateType` |
