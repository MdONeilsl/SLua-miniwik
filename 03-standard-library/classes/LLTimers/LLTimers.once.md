# `LLTimers.once`

```lua
LLTimers.once(self, seconds: number, callback: LLTimerOnceCallback) -> LLTimerCallback
```

Registers a one-time timer. The timer runs only once and is automatically removed afterward. The callback receives (expected_time, nil). Returns the same function passed in, which can be used to cancel it early via LLTimers:off().

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `seconds` | `number` | Time in seconds to wait before triggering. A value of 0 schedules it for the next frame. |
| `callback` | `LLTimerOnceCallback` | Function to execute once when the time arrives. |

**Returns:** `LLTimerCallback`
