# `ll.Dialog`

```lua
ll.Dialog(agent: uuid, msg: string, buttons: {string}, channel: number) -> ()
```

Displays a dialog box on the specified agent’s screen, showing the message and up to 12 selectable buttons. When a button is selected, its label is broadcast as a chat message on the given channel. The chat appears to originate from the object’s location but is attributed to the agent’s name and UUID, allowing it to be received as long as the agent remains within the region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `agent` | `uuid` | UUID of the agent in the same region. |
| `msg` | `string` | Text message to display in the dialog box. |
| `buttons` | `{string}` | A list of up to 12 strings representing button labels. |
| `channel` | `number` | Output chat channel (any 32-bit signed integer value) where button clicks are chatted. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `avatar_communication`, `chat`, `user_interface` |