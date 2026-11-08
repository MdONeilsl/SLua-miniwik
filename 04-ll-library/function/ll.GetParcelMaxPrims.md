# `ll.GetParcelMaxPrims`

```lua
ll.GetParcelMaxPrims(pos: vector, sim_wide: boolean | number) -> number
```

Returns an integer indicating the maximum total land impact (prim count) permitted for objects on the parcel at position `pos`, with the scope either limited to that specific parcel or extended to all parcels owned by the same owner across the region, depending on the value of `sim_wide`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates (the Z component is ignored). |
| `sim_wide` | `boolean | number` | Boolean. If TRUE, returns the combined land impact limit for all parcels owned by the parcel owner in the region; if FALSE, returns only the limit for the specified parcel. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel` |