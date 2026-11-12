# `CHANGED_TELEPORT`

The avatar attached to this object has undergone a teleport. This event fires exclusively within the root prim of an attachment and will not trigger for child prims or when using 'sit teleports'. Furthermore, if scripts are disabled at the intended location, the system queues the event and executes it after moving onto a parcel that permits scripting.

**Type:** `number`

**Value:** `0x200`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `ChangeType` |
