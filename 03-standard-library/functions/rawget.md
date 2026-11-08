# `rawget`

```lua
rawget(t: {[K]: V}, k: K) -> V?
```

Retrieves a value from a table by key, bypassing standard lookup mechanisms like the `__index` metamethod. This ensures direct access to the specified data structure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V}` | The target table where the retrieval operation occurs. |
| `k` | `K` | The identifier used to search for a value within the table. |

**Returns:** `V?`