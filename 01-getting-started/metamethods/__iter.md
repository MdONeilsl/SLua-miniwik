# `__iter`

```lua
__iter<S, K, V...>(self: {}) -> ((state: S, index: K) -> (K?, V...), S, K)
```

When Lua begins generalized iteration over a table or userdata, this method is invoked first. It must provide an iterator function, the necessary state data, and starting control variables for the process.

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | The container that is currently undergoing iteration. |

**Returns:** `((state: S, index: K) -> (K?, V...), S, K)`
