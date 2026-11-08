# `ll.RequestUserKey`

```lua
ll.RequestUserKey(username: string) -> uuid
```

Initiates an asynchronous lookup for the agent's UUID based on their current or past username, yielding NULL_KEY if the agent is not found. The function returns a handle used to track the dataserver query event.

## Arguments

| Name | Type | Description |
|---|---|---|
| `username` | `string` | Current or historical username of the avatar to resolve. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `dataserver`, `uuid` |