# `table.create`

```lua
table.create(n: number, v: V) -> {V}
```

Constructs a new table and reserves space for array elements. This capacity reservation helps arrays but does not improve dictionary performance.

## Arguments

| Name | Type | Description |
|---|---|---|
| `n` | `number` | The desired count for allocated items. |
| `v` | `V?` | Value used to initialize every element slot. |

**Returns:** `{V}`
