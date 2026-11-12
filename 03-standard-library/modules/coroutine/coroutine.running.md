# `coroutine.running`

```lua
coroutine.running() -> thread?
```

Retrieves the coroutine that is presently executing. If this function is invoked while running in the main program context, it will return nil.

**Returns:** `thread?`
