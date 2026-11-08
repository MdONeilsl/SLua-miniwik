# `OBJECT_BODY_SHAPE_TYPE`

This flag must be used with ll.GetObjectDetails when you need to fetch a float value that indicates the gender or sex configuration of an avatar's shape (where 0.0 signifies standard female, 1.0 signifies standard male, and any value at or above 0.5 is treated as male). If the target object is not an avatar or if no corresponding data exists, the function will return -1.0.

**Type:** `number`

**Value:** `26`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectDetailsParam` |