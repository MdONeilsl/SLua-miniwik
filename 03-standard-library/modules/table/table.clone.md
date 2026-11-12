# `table.clone`

```lua
table.clone(t: table) -> table
```

This function generates a shallow duplicate of the input table, transferring its associated metatable, keys, and values. The resulting copy is guaranteed to be unfrozen regardless of whether the original was locked.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `table` | The source table that needs to be duplicated. |

**Returns:** `table`
