# `email`

```lua
email(time: string, address: string, subject: string, msg: string, num_left: number) -> ()
```

When a message is retrieved using `ll.GetNextEmail()`, this event fires. The arguments provide details about the sender, content, and remaining messages in the queue.

## Arguments

| Name | Type | Description |
|---|---|---|
| `time` | `string` | The time the message arrived, formatted as a string. |
| `address` | `string` | The unique electronic mail identifier for who sent it. |
| `subject` | `string` | A brief title describing the message content. |
| `msg` | `string` | The main written content or body of the correspondence. |
| `num_left` | `number` | How many messages remain available for retrieval. |

**Returns:** `()`
