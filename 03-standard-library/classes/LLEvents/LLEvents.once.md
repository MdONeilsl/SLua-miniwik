# `LLEvents.once`

```lua
LLEvents.once(self, event: LLEventName, callback: LLEventHandler) -> LLEventHandler
```

Registers a one-time event handler. The function runs only once and is automatically removed afterward. Returns a newly generated wrapper function, which MUST be used if you want to manually remove the handler early using LLEvents:off().

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `event` | `LLEventName` | Name of the event to handle. |
| `callback` | `LLEventHandler` | Function to execute once when the event happens. |

**Returns:** `LLEventHandler`
