# `pcall`

```lua
pcall(f: (A...) -> R..., ...) -> (boolean, R...)
```

This function executes `f` safely using provided arguments. It returns a boolean indicating whether the call succeeded; if successful, it provides results, otherwise, it gives an error message.

## Arguments

| Name | Type | Description |
|---|---|---|
| `f` | `(A...) -> R...` | The callable function itself. |
| `...` | `A...` | Values passed into the specified procedure. |

**Returns:** `(boolean, R...)`
