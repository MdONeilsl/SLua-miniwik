# `control`

```lua
control(id: uuid, level: number, edge: number) -> ()
```

This function executes when the script receives data about an avatar's controlled movements. It supplies two bitfield values: one showing currently pressed buttons, and another detailing which buttons recently transitioned states.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | The unique identifier for the controlled avatar. |
| `level` | `number` | Bitmask showing which actions are currently being maintained. |
| `edge` | `number` | Bitmask detailing which input buttons recently switched status. |

**Returns:** `()`
