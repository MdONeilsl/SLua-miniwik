# `ll.ListenControl`

```lua
ll.ListenControl(handle: number, active: boolean | number) -> ()
```

Activates or deactivates the listener identified by the given integer handle. When active is set to TRUE, the listener becomes active; when set to FALSE, it is turned off.


## Arguments

| Name | Type | Description |
|---|---|---|
| `handle` | `number` | Integer listener handle returned by ll.Listen. |
| `active` | `boolean | number` | Boolean. If TRUE, activates the listener; if FALSE, deactivates it. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar_communication`, `chat`, `script_communication` |