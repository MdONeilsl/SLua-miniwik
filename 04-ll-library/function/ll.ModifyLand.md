# `ll.ModifyLand`

```lua
ll.ModifyLand(action: number, brush: number) -> ()
```

Applies a terrain modification based on the provided land action and brush scale (0, 1, or 2, denoting 2m x 2m, 4m x 4m, or 8m x 8m respectively).


## Arguments

| Name | Type | Description |
|---|---|---|
| `action` | number | LAND_* action flag to perform (e.g., LAND_LEVEL, LAND_RAISE, LAND_LOWER, LAND_SMOOTH, LAND_NOISE, or LAND_REVERT). |
| `brush` | number | Brush size (0, 1, or 2, representing 2m x 2m, 4m x 4m, or 8m x 8m). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `region` |