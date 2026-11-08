# `ll.RegionSayTo`

```lua
ll.RegionSayTo(target: uuid, channel: number, msg: string) -> ()
```

Transmits the specified message to the designated agent or object within the same region, using the given channel for private communication. When the target is an agent and the channel is non-zero, any attachments worn by that avatar will also receive the message.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target agent or prim in the same region. |
| `channel` | `number` | Chat channel (any 32-bit signed integer value) to chat the message on. |
| `msg` | `string` | Text message string to send. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication`, `chat`, `script_communication` |