# `ll.LinkSetSoundRadius`

```lua
ll.LinkSetSoundRadius(link: number, radius: number) -> ()
```

Sets the maximum audible range in meters for sounds triggered or attached to the specified link, restricting how far away listeners can hear them.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `radius` | `number` | Maximum distance in meters at which the sounds can be heard. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |