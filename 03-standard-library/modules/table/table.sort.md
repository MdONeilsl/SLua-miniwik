# `table.sort`

```lua
table.sort(a: {V}, f: ((a: V, b: V) -> boolean)?) -> ()
```

This function arranges the elements of a given table sequentially within that same structure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | The table containing elements that need ordering. |
| `f` | `((a: V, b: V) -> boolean)?` | A routine used to compare two elements. |

**Returns:** `()`