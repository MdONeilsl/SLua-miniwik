# `link_message`

```lua
link_message(sender_num: number, num: number, str: string, id: string) -> ()
```

This function executes when the script receives linked communication from another script. The arguments passed include numerical, textual, and key data.

## Arguments

| Name | Type | Description |
|---|---|---|
| `sender_num` | `number` | The link number identifying the sending object's script. |
| `num` | `number` | A whole number transmitted by the originating script. |
| `str` | `string` | Any textual data sent from the source script. |
| `id` | `string` | A unique identifier provided by the sender. |

**Returns:** `()`
