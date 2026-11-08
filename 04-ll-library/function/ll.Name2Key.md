# `ll.Name2Key`

```lua
ll.Name2Key(name: string) -> uuid
```

This function retrieves the UUID key for an avatar based on their name within the current region. If no matching agent is found, it returns NULL_KEY. Accepted name formats include 'First Last' or 'first.last', with 'Resident' assumed if the last name is missing; matching is case-insensitive.


## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | string | Name of the avatar (e.g., 'First Last' or 'first.last'). |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |