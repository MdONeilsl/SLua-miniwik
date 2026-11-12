# `ll.ScaleByFactor`

```lua
ll.ScaleByFactor(scaling_factor: number) -> boolean
```

Tries to resize the whole object uniformly using the scaling_factor while preserving the relative sizes and positions of its prims. The operation will fail if the linkset is physical, if it's a pathfinding character, if it's in keyframed motion, if the resulting scale exceeds prim or linkability limits, or if the new size would exceed the parcel’s capacity.

## Arguments

| Name | Type | Description |
|---|---|---|
| `scaling_factor` | `number` | Multiplier scale factor to apply to the prim sizes and their local positions. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |
