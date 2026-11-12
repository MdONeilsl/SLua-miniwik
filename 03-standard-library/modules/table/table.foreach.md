# `table.foreach`

```lua
table.foreach(t: {[K]: V}, f: (key: K, value: V) -> R?) -> R?
```

This method processes every stored pair of keys and values within a given table structure. Note that this function is deprecated for use.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V}` | The collection whose contents should be traversed. |
| `f` | `(key: K, value: V) -> R?` | The routine executed for every stored entry. |

**Returns:** `R?`
