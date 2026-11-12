# `ll.SetObjectPermMask`

```lua
ll.SetObjectPermMask(group: number, flags: number) -> ()
```

Configures the permission flags for the script's object based on the provided group.


## Arguments

| Name | Type | Description |
|---|---|---|
| `group` | `number` | MASK_* group (e.g., MASK_BASE, MASK_OWNER, MASK_GROUP, MASK_EVERYONE, or MASK_NEXT) to set. |
| `flags` | `number` | Bitfield of permissions (PERM_* flags) to set. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `asset_permissions`, `linkset` |
