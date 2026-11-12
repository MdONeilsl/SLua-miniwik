# `ll.GetParcelPrimCount`

```lua
ll.GetParcelPrimCount(pos: vector, category: number, sim_wide: boolean | number) -> number
```

Returns an integer indicating the cumulative land impact of objects located on the parcel at position `pos`, filtered by the given category. When `sim_wide` is set to TRUE, the result reflects the aggregated usage across all parcels within the region that are owned by the target parcel’s owner; otherwise, it returns the usage limited to the specific parcel only.


## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates (the Z component is ignored). |
| `category` | `number` | PARCEL_COUNT_* category flag. |
| `sim_wide` | `boolean | number` | Boolean. If TRUE, searches all parcels in the region owned by the targeted parcel's owner; if FALSE, searches only the specified parcel. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel` |
