# `table.extend`

```lua
table.extend(a: {V}, b: {V}) -> {V}
```

Appends every element from `b` to the end of `a`, repositioning `a`’s elements to make space. Equivalent to shifting `b`’s contents into `a` starting at its final index.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | Target array that receives appended elements. |
| `b` | `{V}` | Source array whose elements are added to `a`. |

**Returns:** `{V}`
