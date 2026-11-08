# `ll.RemoteLoadScriptPin`

```lua
ll.RemoteLoadScriptPin(target: uuid, script: string, pin: number, running: boolean | number, start_param: number) -> ()
```

When invoked, this function transfers a script from the caller’s inventory to the specified target prim, initiating its execution if the running flag is true and passing the start_param value. The operation succeeds only if the script’s owner possesses modify permissions on the target and the target’s PIN exactly matches the pin value previously configured using ll.SetRemoteScriptAccessPin.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target prim in the same region. |
| `script` | `string` | Name of the script in the prim's inventory. |
| `pin` | `number` | Integer PIN code (must match the PIN set on the ObjectID via ll.SetRemoteScriptAccessPin). |
| `running` | `boolean | number` | Boolean. If TRUE, sets the copied script to run immediately; if FALSE, leaves it stopped. |
| `start_param` | `number` | Integer start parameter passed to the copied script (readable via ll.GetStartParameter). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `3.0` |
| `categories` | `prim`, `prim_inventory`, `script` |