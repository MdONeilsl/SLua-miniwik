# `rawset`

```lua
rawset(t: {[K]: V}, k: K, v: V) -> {[K]: V}
```

This function sets a specific key/value pair within a table structure. It achieves this by ignoring any custom behavior defined in the `__newindex` metamethod.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V}` | The target table where the key/value pair will be placed. |
| `k` | `K` | The specific key under which the data will be stored. |
| `v` | `V` | The content that will be set at the specified key. |

**Returns:** `{[K]: V}`
