# `table.freeze`

```lua
table.freeze(t: table) -> table
```

This function sets the table to read-only status, effectively freezing it. Be aware that this operation is shallow and will not modify nested tables; furthermore, calling it fails if the target already has a frozen state or protected metatable.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `table` | The specific table instance targeted for immutability. |

**Returns:** `table`