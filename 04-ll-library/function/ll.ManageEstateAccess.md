# `ll.ManageEstateAccess`

```lua
ll.ManageEstateAccess(action: number, avatar: uuid) -> boolean
```

Performs an action—adding or removing avatars or groups—from the estate’s access or ban lists, as determined by the provided action flag. Returns TRUE upon success, or FALSE if the operation is throttled, the action is invalid, or the script owner does not have estate management permissions.


## Arguments

| Name | Type | Description |
|---|---|---|
| `action` | `number` | An ESTATE_ACCESS_* action flag specifying the operation to perform. |
| `avatar` | `uuid` | UUID of the avatar or group to add or remove. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `land_moderation` |
