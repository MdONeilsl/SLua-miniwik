# `coroutine.create`

```lua
coroutine.create(f: (...any) -> ...any) -> thread
```

Creates a new coroutine object that will execute the specified function when it is resumed.

## Arguments

| Name | Type | Description |
|---|---|---|
| `f` | `(...any) -> ...any` | The routine to be run by the newly created coroutine. |

**Returns:** `thread`