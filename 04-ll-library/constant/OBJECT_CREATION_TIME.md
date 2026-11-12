# `OBJECT_CREATION_TIME`

This flag must be utilized with ll.GetObjectDetails when you need to retrieve the object's creation time. This time is determined either through build-menu rezzing or mesh uploads, and not by means of inventory/script rezzes, copying, or modification. Note that an empty string will be returned if the target is an avatar.

**Type:** `number`

**Value:** `36`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectDetailsParam` |
