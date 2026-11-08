# `coroutine.status`

```lua
coroutine.status(co: thread) -> "running" | "suspended" | "normal" | "dead"
```

Determines and reports the current execution state of a given coroutine object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `co` | `thread` | The coroutine object whose current operational status is desired. |

**Returns:** `"running" | "suspended" | "normal" | "dead"`