# `next`

```lua
next(t: {[K]: V}, i: K?) -> (K?, V)
```

The function yields the subsequent key and value found during table iteration. If no starting index is provided or if `nil` is passed for the index, it retrieves the very first pair available.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V}` | The collection whose elements are being examined. |
| `i` | `K?` | Specifies a key; omitting it or using nil fetches the initial entry. |

**Returns:** `(K?, V)`