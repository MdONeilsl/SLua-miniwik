# `ll.GetExperienceDetails`

```lua
ll.GetExperienceDetails(experience_id: uuid) -> {any}
```

For the given experience_id, this function returns a list containing the experience's name, its owner's ID, the experience's unique identifier, its current state as an integer, a descriptive message for that state, and the group ID associated with it.


## Arguments

| Name | Type | Description |
|---|---|---|
| `experience_id` | uuid | UUID of the experience to query (can be NULL_KEY to retrieve details for the script's own experience). |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `experience` |
