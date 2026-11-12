# `listen`

```lua
listen(channel: number, name: string, id: uuid, msg: string) -> ()
```

This function executes when a chat message arrives that matches active filters on a specific channel. The handler receives details about the sender, including their name, unique ID, and the spoken text content.

## Arguments

| Name | Type | Description |
|---|---|---|
| `channel` | `number` | The chat channel in which the communication occurred. |
| `name` | `string` | Either the object's current name or its old identifier. |
| `id` | `uuid` | Unique identifier for the originating avatar or object. |
| `msg` | `string` | The actual textual content spoken by the sender. |

**Returns:** `()`
