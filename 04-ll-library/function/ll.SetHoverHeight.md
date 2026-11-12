# `ll.SetHoverHeight`

```lua
ll.SetHoverHeight(height: number, water: boolean | number, tau: number) -> ()
```

Dampens the object’s vertical motion to maintain a hover at the specified height—above ground or water (if water is true)—within tau seconds. This function is not intended for use with vehicles; to stop hovering, use ll.StopHover.

## Arguments

| Name | Type | Description |
|---|---|---|
| `height` | `number` | Distance to hover above the ground or water. |
| `water` | `boolean | number` | Boolean. If TRUE, hovers above water too; if FALSE, water is ignored. |
| `tau` | `number` | Timescale in seconds to critically damp the movement. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |
