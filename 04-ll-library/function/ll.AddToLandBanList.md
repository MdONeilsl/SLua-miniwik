# `ll.AddToLandBanList`

```lua
ll.AddToLandBanList(avatar: uuid, hours: number) -> ()
```

Places the specified avatar onto the parcel’s ban list for the given duration in hours; setting the duration to zero results in an indefinite ban. When a banned user attempts to teleport to the parcel, they are instead sent to an adjacent parcel, and the system will not accept durations shorter than 0.01 hours (roughly 36 seconds).

## Arguments

| Name | Type | Description |
|---|---|---|
| `avatar` | `uuid` | UUID of the avatar to add to the ban list. |
| `hours` | `number` | Duration, in hours, to ban the avatar for (0 for indefinite). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `land_moderation`, `parcel` |
