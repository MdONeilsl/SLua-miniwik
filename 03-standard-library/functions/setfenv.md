# `setfenv`

```lua
setfenv(target: number | (T...) -> R..., env: {[string]: any}) -> ((T...) -> R...)?
```

This function establishes a local execution context for the provided callable.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `number | (T...) -> R...` | The function or value for which the scope will be configured. |
| `env` | `{[string]: any}` | A map containing key-value pairs defining the local variables. |

**Returns:** `((T...) -> R...)?`