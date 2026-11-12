# `CHARACTER_STAY_WITHIN_PARCEL`

Specifies if a character must remain confined to its initial designated area (the default setting is FALSE). When set to TRUE, the perimeter of the parcel functions as directional barriers; consequently, the character loses the ability to depart freely and all pathfinding routines (such as wander, flee, evade, or pursue) will limit their chosen destinations exclusively to points inside the parcel. Though it can re-enter if forced outside, voluntary exit remains impossible.

**Type:** `number`

**Value:** `15`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `CharacterParam` |
