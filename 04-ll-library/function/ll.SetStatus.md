# `ll.SetStatus`

```lua
ll.SetStatus(status: number, value: boolean | number) -> ()
```

Assigns the specified status flags, indicated by the bitmask `status`, to the given `value`, which determines whether the status is enabled or disabled.

## Arguments

| Name | Type | Description |
|---|---|---|
| `status` | `number` | Bitmask representing the STATUS_* flag(s) to change. |
| `value` | `boolean | number` | Boolean. If TRUE, enables the status; if FALSE, disables it. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `physics`, `prim_properties` |
