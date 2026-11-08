# `ll.CreateLink`

```lua
ll.CreateLink(target: uuid, parent: boolean | number) -> ()
```

Tries to establish a link between the script's containing object and the specified target object. This operation demands the PERMISSION_CHANGE_LINKS runtime permission to execute.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target prim/object in the same region. |
| `parent` | `boolean | number` | Boolean. If TRUE, the script's object becomes the root prim; if FALSE, target becomes the root. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `linkset` |