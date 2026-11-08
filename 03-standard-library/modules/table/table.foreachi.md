# `table.foreachi`

```lua
table.foreachi(a: {V}, f: (index: number, value: V) -> R?) -> R?
```

Iterates sequentially through each index-value pair in the given array, invoking the provided function for every element.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | Collection to traverse by index and value. |
| `f` | `(index: number, value: V) -> R?` | Callback executed per index-value combination. |

**Returns:** `R?`