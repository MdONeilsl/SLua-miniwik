# `ll.MessageLinked`

```lua
ll.MessageLinked(link: number, num: number, str: string | uuid, id: string | uuid) -> ()
```

Initiates a link_message event, forwarding the values num, str, and id to the scripts residing in the prim(s) designated by link, enabling communication between scripts within the same object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag controlling which prim(s) receive the message. |
| `num` | `number` | An integer value passed as the second parameter of the link_message event. |
| `str` | `string | uuid` | A string value passed as the third parameter of the link_message event. |
| `id` | `string | uuid` | A key value passed as the fourth parameter of the link_message event. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `script_communication` |
