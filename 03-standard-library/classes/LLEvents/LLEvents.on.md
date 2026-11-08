# `LLEvents.on`

```lua
LLEvents.on(self, event: LLEventName, callback: LLEventHandler) -> LLEventHandler
```

Registers a handler function to run whenever the specified event occurs. Multiple handlers can be attached to the same event and will run in the order they were added. Returns the same function passed in so it can be used later with LLEvents:off().

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `event` | `LLEventName` | Name of the event to handle. |
| `callback` | `LLEventHandler` | Function to execute when the event happens. |

**Returns:** `LLEventHandler`
