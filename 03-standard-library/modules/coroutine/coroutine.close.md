# `coroutine.close`

```lua
coroutine.close(co: thread) -> (boolean, string?)
```

This function terminates a specified coroutine. It signals success by returning true, or failure along with an error message if the closure fails.

## Arguments

| Name | Type | Description |
|---|---|---|
| `co` | `thread` | The specific coroutine object intended for closure. |

**Returns:** `(boolean, string?)`
