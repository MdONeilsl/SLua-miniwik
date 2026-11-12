# `ll.LinkSetSoundQueueing`

```lua
ll.LinkSetSoundQueueing(link: number, queue: boolean | number) -> ()
```

Controls whether sound queuing is active for the specified linked prim. With `queue` set to TRUE, sounds are queued and played one after another.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `queue` | `boolean | number` | Boolean. If TRUE, sound queuing is enabled; if FALSE, it is disabled. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
