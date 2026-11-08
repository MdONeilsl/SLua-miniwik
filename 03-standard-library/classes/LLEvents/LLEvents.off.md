# `LLEvents.off`

```lua
LLEvents.off(self, event: LLEventName, callback: LLEventHandler) -> boolean
```

Removes an event handler. If the function was added multiple times via LLEvents:on(), only the last one added is removed. Returns true if the function was found and removed, false otherwise.

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `event` | `LLEventName` | Name of the event to remove. |
| `callback` | `LLEventHandler` | Function to remove. Note: To remove a handler added via LLEvents:once(), you must pass the specific wrapper function it returned. |

**Returns:** `boolean`
