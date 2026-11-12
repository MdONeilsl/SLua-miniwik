# `pairs`

```lua
pairs(t: {[K]: V}) -> (({[K]: V}, K?) -> (K?, V), {[K]: V}, K)
```

This function generates a mechanism to traverse all stored pairs of keys and values contained in the specified table.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V}` | The container structure whose contents should be traversed. |

**Returns:** `(({[K]: V}, K?) -> (K?, V), {[K]: V}, K)`
