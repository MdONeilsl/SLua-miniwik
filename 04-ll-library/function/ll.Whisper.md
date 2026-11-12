# `ll.Whisper`

```lua
ll.Whisper(channel: number, msg: string) -> ()
```

Sends the message `msg` to any scripts or agents subscribed to `channel` within the whisper range defined by `ll.GetEnv("whisper_range")`, typically 10 meters in most regions. Agents automatically receive messages on `PUBLIC_CHANNEL` (0) and `DEBUG_CHANNEL` (2147483647). Channels other than these are reserved for direct script-to-script communication.

## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | number | Chat channel (any 32-bit signed integer value) to whisper the message on. |
| `msg` | string | Text message string to broadcast. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication`, `chat`, `script_communication` |
