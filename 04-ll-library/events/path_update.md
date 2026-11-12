# `path_update`

```lua
path_update(type: number, reserved: {any}) -> ()
```

This event fires when the status of a pathfinding character is updated, indicating either successful progress or an encountered failure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `type` | `number` | Indicates the current pathfinding status or error code. |
| `reserved` | `{any}` | A placeholder variable that is not currently used. |

**Returns:** `()`
