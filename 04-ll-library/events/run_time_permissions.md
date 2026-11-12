# `run_time_permissions`

```lua
run_time_permissions(perm: number) -> ()
```

Event fires when an agent alters runtime permissions requested via ll.RequestPermissions. It provides the active integer bitfield of granted rights in `perm`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `perm` | `number` | The combined set of currently active permission flags. |

**Returns:** `()`
