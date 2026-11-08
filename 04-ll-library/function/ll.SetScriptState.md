# `ll.SetScriptState`

```lua
ll.SetScriptState(script: string, running: boolean | number) -> ()
```

Configures whether the specified script within the prim’s inventory is active or inactive; setting `running` to TRUE activates it, while FALSE deactivates it.


## Arguments

| Name | Type | Description |
|---|---|---|
| `script` | `string` | Name of the script in the prim's inventory. |
| `running` | `boolean | number` | Boolean. If TRUE, enables the script; if FALSE, disables it. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim_inventory`, `script` |