# `OBJECT_DAMAGE_TYPE`

Use this flag when calling `ll.GetObjectDetails` if you need to determine what kind of damage an object (prim) applies during a collision event. The function will return an integer that corresponds either to a predefined `DAMAGE_TYPE_*` constant, a user-defined type, or any value utilized by a combat system.

**Type:** `number`

**Value:** `52`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectDetailsParam` |