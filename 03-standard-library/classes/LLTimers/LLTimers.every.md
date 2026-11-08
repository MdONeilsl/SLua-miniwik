# `LLTimers.every`

```lua
LLTimers.every(self, seconds: number, callback: LLTimerEveryCallback) -> LLTimerCallback
```

Registers a repeating timer. The callback receives (expected_time, interval). Returns the same function passed in so it can be removed later.

**Available in:** SLua yes · LSL yes

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | — | — |
| `seconds` | `number` | Interval in seconds. Minimum practical interval is ~0.022s (one server frame). An interval of 0 schedules the timer for the next frame. |
| `callback` | `LLTimerEveryCallback` | Function to execute when the time arrives. |

**Returns:** `LLTimerCallback`
