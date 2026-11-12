# `ll.ReturnObjectsByOwner`

```lua
ll.ReturnObjectsByOwner(owner: uuid, scope: number) -> number
```

This function retrieves objects belonging to the specified owner within a given scope—such as a parcel, its owner, or a region. It demands the PERMISSION_RETURN_OBJECTS permission, and the script’s owner must either own the parcel or hold the role of estate manager or region owner.


## Arguments

| Name | Type | Description |
|---|---|---|
| `owner` | `uuid` | UUID of the avatar or group whose objects will be returned. |
| `scope` | `number` | OBJECT_RETURN_* scope flag (such as OBJECT_RETURN_PARCEL, OBJECT_RETURN_PARCEL_OWNER, or OBJECT_RETURN_REGION). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `land_moderation`, `rez` |
