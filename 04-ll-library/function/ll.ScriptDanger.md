# `ll.ScriptDanger`

```lua
ll.ScriptDanger(pos: vector) -> boolean
```

Returns 1 if the specified position is located on public land, sandbox land, land with restricted edit or build permissions, or land that prevents external scripts from running.


## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates to check. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel`, `script` |
