# `setmetatable`

```lua
setmetatable(t: T, mt: MT) -> setmetatable<T, MT>
```

This function modifies the associated metatable of a specified table. An exception will be raised if the target table already possesses a protected metatable (i.e., it contains a `__metatable` field).

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `T` | The table whose associated metatable needs modification. |
| `mt` | `MT` | The new metatable that will be assigned. |

**Returns:** `setmetatable<T, MT>`