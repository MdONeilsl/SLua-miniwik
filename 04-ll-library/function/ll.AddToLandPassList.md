# `ll.AddToLandPassList`

```lua
ll.AddToLandPassList(avatar: uuid, hours: number) -> ()
```

Places the specified avatar onto the land pass list for the given duration in hours; if the duration is set to zero, the access remains active indefinitely.


## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar to add to the pass list. |
| `hours` | `number` | Duration, in hours, to allow the avatar for (range [0.0, 144.0], 0 for indefinite). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `land_moderation`, `parcel` |