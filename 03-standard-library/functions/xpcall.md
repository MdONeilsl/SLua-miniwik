# `xpcall`

```lua
xpcall(f: (A...) -> R1..., err: (E) -> R2..., ...) -> (boolean, R1...)
```

This function executes the primary callable `f` using supplied parameters. If execution fails, control is passed to the specified error handling routine, `err`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `f` | `(A...) -> R1...` | Routine that is meant to be executed. |
| `err` | `(E) -> R2...` | Routine that processes any encountered error. |
| `...` | `A...` | Inputs provided for the primary function call. |

**Returns:** `(boolean, R1...)`