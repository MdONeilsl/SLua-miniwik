# `coroutine.yield`

```lua
coroutine.yield(...) -> ...any
```

Pauses execution of the current coroutine, allowing control to pass while delivering specified arguments to the code that resumes it.

## Arguments

| Name | Type | Description |
|---|---|---|
| `...` | `...any` | Data that should be provided when execution continues. |

**Returns:** `...any`
