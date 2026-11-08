# `ll.SetLinkSitFlags`

```lua
ll.SetLinkSitFlags(link: number, flags: number) -> ()
```

Configures the sit target flags for the specified prim link within the linkset.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `flags` | `number` | A bitfield of sit flags (SIT_FLAG_*) to apply. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `sit` |