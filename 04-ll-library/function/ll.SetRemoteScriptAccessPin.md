# `ll.SetRemoteScriptAccessPin`

```lua
ll.SetRemoteScriptAccessPin(pin: number) -> ()
```

Configures the prim to require the specified PIN for remote script loading; a non-zero PIN allows access through ll.RemoteLoadScriptPin, while zero disables this functionality entirely.


## Arguments

| Name | Type | Description |
|---|---|---|
| `pin` | `number` | Integer PIN code (non-zero enables, zero disables). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `prim_inventory`, `script` |