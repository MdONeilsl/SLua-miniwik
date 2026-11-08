# `ll.ReturnObjectsByID`

```lua
ll.ReturnObjectsByID(objects: {uuid}) -> number
```

This function retrieves the specified objects, identified by their UUIDs, and returns them to their respective owners. It demands the PERMISSION_RETURN_OBJECTS permission, and the script's owner must either own the parcel or hold the role of estate manager or region owner.


## Arguments

| Name | Type | Description |
|---|---|---|
| `objects` | `{uuid}` | A list of object UUID keys to return. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `land_moderation`, `rez` |