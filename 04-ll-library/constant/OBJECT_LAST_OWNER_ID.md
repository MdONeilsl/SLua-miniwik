# `OBJECT_LAST_OWNER_ID`

When utilizing ll.GetObjectDetails, this flag retrieves the unique key associated with the object's previous owner. If the object belongs to a group, it specifies the avatar that deeded ownership. The function will return NULL_KEY if the item is an avatar, was never transferred, or was moved to inventory and subsequently re-rezzed.

**Type:** `number`

**Value:** `27`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ObjectDetailsParam` |
