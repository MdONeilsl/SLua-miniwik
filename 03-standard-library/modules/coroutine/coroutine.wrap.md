# `coroutine.wrap`

```lua
coroutine.wrap(f: (...any) -> ...any) -> (...any) -> ...any
```

This utility wraps a given function into a coroutine object. It then returns a new callable wrapper that manages the execution flow of the underlying routine.

## Arguments

| Name | Type | Description |
|---|---|---|
| `f` | `(...any) -> ...any` | The routine whose execution needs to be managed by a coroutine. |

**Returns:** `(...any) -> ...any`
