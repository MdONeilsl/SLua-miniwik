# `coroutine.resume`

```lua
coroutine.resume(co: thread, ...) -> (boolean, ...any)
```

This method restarts execution of the specified coroutine. It returns a boolean indicating success or failure, along with any values yielded or returned by the resumed routine.

## Arguments

| Name | Type | Description |
|---|---|---|
| `co` | `thread` | The coroutine that needs to be restarted. |
| `...` | `...any` | Values provided when restarting the routine. |

**Returns:** `(boolean, ...any)`
