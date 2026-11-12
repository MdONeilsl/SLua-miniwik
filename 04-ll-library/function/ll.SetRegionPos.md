# `ll.SetRegionPos`

```lua
ll.SetRegionPos(position: vector) -> boolean
```

Attempts to reposition the entire object such that its root prim is located within 0.1m of the specified vector position (with underground positions adjusted to ground level). Returns 1 for success or 0 for failure.


## Arguments

| Name | Type | Description |
|---|---|---|
| `position` | `vector` | Target position vector in region coordinates (can cross up to 10m over a region border). |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `prim` |
