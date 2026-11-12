# `table.shrink`

```lua
table.shrink(t: {V}, shrink_sparse: boolean?) -> {V}
```

Reduces the table’s memory footprint to the smallest possible size, optionally reorganizing sparse elements into hash storage for efficiency.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{V}` | Table to compact and optimize for memory. |
| `shrink_sparse` | `boolean?` | If true, permits relocating sparse array entries into hash-mode storage. |

**Returns:** `{V}`
