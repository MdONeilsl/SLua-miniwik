# `table.find`

```lua
table.find(t: {V}, v: V, i: number?) -> number?
```

Finds the first position where `v` appears in `t`, starting from index `i` (if provided), and returns that index; traversal halts upon encountering the first nil.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{V}` | Array to examine for the target value. |
| `v` | `V` | Item to locate within the table. |
| `i` | `number?` | Optional starting position for the search. |

**Returns:** `number?`