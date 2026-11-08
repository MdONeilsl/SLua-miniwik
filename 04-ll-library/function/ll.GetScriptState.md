# `ll.GetScriptState`

```lua
ll.GetScriptState(script: string) -> boolean
```

Returns an integer value indicating the runtime status of the specified script within the prim's inventory, where 1 signifies the script is active and 0 indicates it is not running.

## Arguments

| Name | Type | Description |
|---|---|---|
| `script` | `string` | Name of the script in the prim's inventory. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim_inventory`, `script` |