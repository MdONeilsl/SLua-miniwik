# `ll.ReplaceEnvironment`

```lua
ll.ReplaceEnvironment(position: vector, environment: string | uuid, track_no: number, day_length: number, day_offset: number) -> number
```

Sets the environmental setting for the parcel at the given position (or for the entire region if the position is <-1.0, -1.0, -1.0>) corresponding to the specified track_no. Updates day_length and day_offset if provided. Requires either parcel editing permissions or estate management privileges.

## Arguments

| Name | Type | Description |
|---|---|---|
| `position` | `vector` | Position vector of the target parcel (the Z component is ignored; use <-1.0, -1.0, -1.0> for the entire region). |
| `environment` | `string | uuid` | Name of an environmental setting in inventory, or its asset UUID (or empty string/NULL_KEY to clear). |
| `track_no` | `number` | The elevation track to change (0: water, 1: ground, 2: 1000m, 3: 2000m, 4: 3000m, -1: all tracks). |
| `day_length` | `number` | Day cycle length in seconds (-1 to leave unchanged). |
| `day_offset` | `number` | Day cycle offset in seconds from UTC (-1 to leave unchanged). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel`, `parcel_appearance` |
