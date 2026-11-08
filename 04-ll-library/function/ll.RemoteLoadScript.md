# `ll.RemoteLoadScript`

```lua
ll.RemoteLoadScript(target: uuid, script: string, running: boolean | number, start_param: number) -> ()
```

No longer supported.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target prim. |
| `script` | `string` | Name of the script in the prim's inventory. |
| `running` | `boolean | number` | Boolean. If TRUE, sets the copied script to run immediately; if FALSE, leaves it stopped. |
| `start_param` | `number` | Integer start parameter passed to the copied script (readable via ll.GetStartParameter). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `prim_inventory`, `script` |