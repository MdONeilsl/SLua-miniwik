# `ll.Shout`

```lua
ll.Shout(channel: number, msg: string) -> ()
```

Sends the message `msg` to all scripts or agents subscribed to `channel` within the range specified by `ll.GetEnv("shout_range")`, typically 100 meters in most regions. Agents receive messages on `PUBLIC_CHANNEL` (0) and `DEBUG_CHANNEL` (2147483647). Channels other than these are reserved for direct script-to-script communication.

## Arguments

| Name | Type | Description |
|---|---|---|
| channel | number | Chat channel (any 32-bit signed integer value) to shout the message on. |
| msg | string | Text message string to broadcast. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `avatar_communication`, `chat`, `script_communication` |