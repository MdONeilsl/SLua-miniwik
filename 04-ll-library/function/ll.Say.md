# `ll.Say`

```lua
ll.Say(channel: number, msg: string) -> ()
```

Sends the message `msg` to all scripts or agents that are within the chat range defined by `ll.GetEnv("chat_range")`, typically 20 meters in most regions. Agents receive messages on `PUBLIC_CHANNEL` (0) and `DEBUG_CHANNEL` (2147483647). All other channels are designated for communication between scripts.

## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `number` | Chat channel (any 32-bit signed integer value) to chat the message on. |
| `msg` | `string` | Text message string to broadcast. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication`, `chat`, `script_communication` |