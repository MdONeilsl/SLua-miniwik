# `ll.RegionSay`

```lua
ll.RegionSay(channel: number, msg: string) -> ()
```

Sends the specified message to all active scripts subscribed to the given channel within the current region. The PUBLIC_CHANNEL (0) is not supported, ensuring messages are received only by other scripts.

## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `number` | Chat channel (any 32-bit signed integer value except zero) to chat the message on. |
| `msg` | `string` | Text message string to broadcast. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `chat`, `script_communication` |