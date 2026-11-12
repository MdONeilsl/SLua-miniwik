# `ll.SetEnvironment`

```lua
ll.SetEnvironment(position: vector, params: list) -> number
```

Sets environmental properties at the specified position for a parcel, or for the entire region if the position is <-1.0, -1.0, z>, by applying the values in the params list. If params is empty, any prior overrides are cleared.


## Arguments

| Name | Type | Description |
|---|---|---|
| `position` | `vector` | Position vector in region coordinates to specify the target parcel, or <-1.0, -1.0, z> for the entire region (where z specifies the sky track, or -1 for all tracks). |
| `params` | `list` | A list of environmental attributes and values to apply (or empty to clear). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel`, `parcel_appearance` |
