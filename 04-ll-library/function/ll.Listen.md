# `ll.Listen`

```lua
ll.Listen(channel: number, name: string, id: uuid, msg: string) -> number
```

Sets up a listener on the specified channel to capture messages matching the given ID, and message content. The function returns an integer handle that can be used to manage or delete the listener. Filters defined by empty strings or NULL_KEY are ignored for their respective parameters.

## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `number` | Chat channel (any 32-bit signed integer value) to listen on. Exact range is -2147483648 to 2147483647. |
| `name` | `string` | Specific prim name or agent legacy name to filter by (or empty string for no filter). |
| `id` | `uuid` | Specific agent or prim UUID to filter by (or NULL_KEY for no filter). |
| `msg` | `string` | Specific chat message string to filter by (or empty string for no filter). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication`, `chat`, `script_communication` |