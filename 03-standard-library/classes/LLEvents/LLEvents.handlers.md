# `LLEvents.handlers`

```lua
LLEvents.handlers(self, event: LLEventName) -> {LLEventHandler}
```

Returns an array table containing all the functions currently handling the specified event. Useful for debugging or for iterating to remove all functions handling an event.

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `event` | `LLEventName` | Name of the event to query. |

**Returns:** `{LLEventHandler}`
