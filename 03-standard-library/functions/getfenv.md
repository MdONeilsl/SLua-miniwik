# `getfenv`

```lua
getfenv(target: ((...any) -> ...any) | number) -> {[string]: any}
```

Retrieves the specific execution context variables associated with a provided function object or numerical identifier.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `((...any) -> ...any) | number` | The callable object or integer index whose environment is desired. |

**Returns:** `{[string]: any}`