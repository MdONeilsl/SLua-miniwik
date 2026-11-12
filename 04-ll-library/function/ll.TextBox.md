# `ll.TextBox`

```lua
ll.TextBox(agent: uuid, msg: string, channel: number) -> ()
```

Displays a text input dialog to the specified agent, showing the given message. When the agent submits text, it is broadcast as a chat message on the designated channel, appearing to originate from the object’s location but attributed to the agent’s name and UUID, allowing it to be received by others in the same region as long as the agent remains present.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the agent in the same region. |
| `msg` | `string` | Text message to display in the text box. |
| `channel` | `number` | Output chat channel (any 32-bit signed integer value) where the input text is chatted. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `avatar_communication`, `chat`, `user_interface` |
