# `LLTimers.off`

```lua
LLTimers.off(self, callback: LLTimerCallback) -> boolean
```

Stops and removes a timer. If the same function was added multiple times, only the last one added is removed, regardless of its interval. Returns true if the timer was found and removed, false otherwise.

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `callback` | `LLTimerCallback` | Function reference to remove. |

**Returns:** `boolean`
