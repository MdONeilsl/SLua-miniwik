# `ll.PassCollisions`

```lua
ll.PassCollisions(pass: number) -> ()
```

Configures whether collision events propagate from child prims to the root prim. When pass is TRUE, events are forwarded; when FALSE (the default), events are confined to the prim where they occur.


## Arguments

| Name | Type | Description |
|---|---|---|
| `pass` | `number` | A PASS_* flag (e.g., PASS_ALWAYS, PASS_IF_NOT_HANDLED, or PASS_NEVER). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `sensor` |