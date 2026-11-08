# `ll.SetBuoyancy`

```lua
ll.SetBuoyancy(buoyancy: number) -> ()
```

Configures the buoyant force applied to a physics-enabled object. When set to 0.0, no buoyancy is applied; values below 1.0 cause the object to sink, 1.0 fully opposes gravitational pull, and values above 1.0 cause the object to ascend.


## Arguments

| Name | Type | Description |
|---|---|---|
| `buoyancy` | `number` | Float buoyancy value to set. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics` |