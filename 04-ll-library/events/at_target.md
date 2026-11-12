# `at_target`

```lua
at_target(tnum: number, targetpos: vector, ourpos: vector) -> ()
```

This function executes when the object's location approaches a predetermined target point, using the unique identifier received from `llTarget`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `tnum` | `number` | The numerical ID associated with the target set via `llTarget`. |
| `targetpos` | `vector` | Coordinates of the location defined when calling `llTarget`. |
| `ourpos` | `vector` | The current coordinates where the scripted object is located. |

**Returns:** `()`
