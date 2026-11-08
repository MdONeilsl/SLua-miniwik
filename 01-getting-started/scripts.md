[README](README.md) · [syntax](syntax.md) · [types](types.md) · [control-flow](control-flow.md) · [functions](functions.md)

# Scripts

How SLua code runs inside a Second Life object. A script is a single compilation unit: the top-level chunk runs once from top to bottom at load, then the script waits and responds to events and timers registered during that first pass. This document covers that lifecycle, the two registration systems (`LLEvents` and `LLTimers`), output, error handling, and a complete working script.

## Contents

- [Script anatomy](#script-anatomy)
- [Printing output](#printing-output)
- [Events](#events)
- [Timers](#timers)
- [Error handling](#error-handling)
- [Errors in event handlers](#errors-in-event-handlers)
- [A complete script](#a-complete-script)
- [Script state and reset](#script-state-and-reset)

## Script anatomy
---
A script has two phases. The top-level chunk runs once when the script starts: declare locals, set up state, register handlers. After the chunk finishes, the script waits. Handlers registered in the chunk run when their events fire; the chunk itself does not run again unless the script is reset or reloaded.

```lua
print("script starting")

local count = 0

LLEvents:on("touch_start", function(events)
    count += 1
    print("touched", count)
end)
```

**Breakdown**

- `print("script starting")` runs once, when the script loads.
- `local count = 0` initialises state visible to every handler defined below.
- `LLEvents:on(...)` registers a handler that runs when the event fires, not now.
- The chunk finishes after the `LLEvents:on` call returns; nothing else runs until an event fires.
- `count` is a local from the chunk, captured by the handler as an upvalue. It survives between handler invocations because the handler holds a reference to it.

## Printing output
---
`print(...)` sends all its arguments as a single line to the object's owner, separated by four spaces. The owner must be in the same region to receive the message. `print` is the primary debugging tool; it is not a chat function; use `ll.Say` for public chat.

```lua
print("hello")
print("score:", 42, true)
```

**Breakdown**

- `print("hello")` sends `hello` to the owner.
- Multiple arguments are joined with four spaces on one line.
- `print` returns nothing; its call value is `nil`.
- The message goes only to the owner, privately; nearby agents do not see it.
- If the owner is not in the region, the message is not delivered. This trips up debugging sessions from a distance.

## Events
---
The event system is `LLEvents`. Register with `LLEvents:on(eventName, callback)`; the callback runs each time the event fires. Multiple handlers can attach to the same event; they run in the order added. `LLEvents:once` registers a handler that removes itself after one call, and `LLEvents:off` removes a previously registered handler.

```lua
local onTouch = LLEvents:on("touch_start", function(events)
    print("touched")
end)

LLEvents:once("touch_start", function(events)
    print("first touch")
end)

LLEvents:off("touch_start", onTouch)
```

**Breakdown**

- `LLEvents:on(event, cb)` registers `cb` for `event` and returns the same function.
- `LLEvents:once(event, cb)` registers a wrapper that removes itself after one call; the wrapper, not `cb`, is the value registered.
- `LLEvents:off(event, cb)` removes a previously registered handler.
- The event name is a string; the set of valid names is documented in 04-ll-library/event.
- To remove a handler registered with `:once`, you must keep the wrapper returned by `:once`; passing the original callback to `:off` does nothing.

## Timers
---
Scheduling is `LLTimers`. `LLTimers:every(seconds, callback)` fires repeatedly; `LLTimers:once(seconds, callback)` fires a single time. Both return a handler reference, which can be passed to `LLTimers:off` to cancel. Timer callbacks receive two parameters: `scheduled_time` (when the timer was logically due) and `interval` (the repeating interval for `every`, `nil` for `once`).

```lua
local tick = LLTimers:every(1.0, function(scheduled: number, interval: number)
    print("tick at", scheduled, "every", interval)
end)

LLTimers:once(5.0, function(scheduled: number)
    print("stopping timer at", scheduled)
    LLTimers:off(tick)
end)
```

**Breakdown**

- `LLTimers:every(1.0, cb)` invokes `cb` every 1 second; `cb` receives the scheduled time and the interval.
- `LLTimers:once(5.0, cb)` invokes `cb` once, 5 seconds from now; `cb` receives only the scheduled time.
- `LLTimers:off(tick)` stops the timer identified by its handler reference.
- The intervals are chosen so the repeating timer fires several times before the one-shot timer cancels it. If the one-shot timer were shorter than the repeating interval, the repeating timer would never print.
- A `seconds` value of `0` schedules for the next frame, but a value around `0.001` is the practical way to request "as soon as possible".
- Do not mix `LLTimers` with legacy timer functions; they share the underlying timer event and will interfere with each other.

## Error handling
---
`error(msg)` raises an error. `pcall(f, ...)` calls `f` in protected mode and returns `true` or `false` followed by results or the error value. `xpcall(f, handler, ...)` calls a handler if `f` raises. `assert(cond, msg)` raises `msg` when `cond` is falsy.

```lua
local ok, err = pcall(function()
    error("something went wrong")
end)
print(ok, err)                    -- false  something went wrong

assert(1 == 1, "unreachable")
```

**Breakdown**

- `error(msg)` raises `msg`. Without an enclosing `pcall` or `xpcall`, the current handler terminates.
- `pcall(f, ...)` returns `true` plus `f`'s results on success, or `false` plus the error value on failure.
- `assert(cond, msg)` raises `msg` when `cond` is falsy; returns `cond` otherwise.
- `xpcall(f, handler, ...)` calls `handler(err)` on failure and returns `handler`'s result as the error value.

## Errors in event handlers
---
An uncaught error inside an event handler is fatal. It terminates the script, not just the handler. The script stops running and stays stopped until it is reset. To survive an error, wrap the handler body in `pcall`.

```lua
LLEvents:on("touch_start", function(events)
    local ok, err = pcall(function()
        error("this is caught")
    end)
    if not ok then
        print("handler caught:", err)
    end
    print("this still runs")
end)
```

**Breakdown**

- `pcall` catches the error raised by `error(...)`.
- `ok` is `false` and `err` holds the message `"this is caught"`.
- The `if not ok` branch prints the error and continues.
- `print("this still runs")` executes because the error was caught.
- Without the `pcall`, the `error(...)` call would terminate the entire script; no later handler and no later event would run.
- Wrap any handler that might fail, especially those that call `ll.*` functions that can raise on invalid input.

## A complete script
---
A working script that combines all of the above: initialisation in the chunk, a repeating timer, a touch handler, and a stop condition.

```lua
print("started")

local touches = 0
local tick = LLTimers:every(1.0, function(scheduled, interval)
    print("uptime tick")
end)

LLEvents:on("touch_start", function(events)
    touches += 1
    print("touched", touches, "time(s)")
    if touches >= 3 then
        LLTimers:off(tick)
        print("stopped timer")
    end
end)
```

**Breakdown**

- `print("started")` runs once when the script loads.
- `LLTimers:every(1.0, ...)` starts a repeating timer before the chunk finishes.
- `LLEvents:on("touch_start", ...)` registers the touch handler; the handler is defined before the chunk finishes.
- The handler increments `touches`, prints the count, and stops the timer after the third touch.
- `touches` and `tick` are locals from the chunk, captured by the two callbacks as upvalues.
- Once `LLTimers:off(tick)` runs, the timer callback never fires again, but the touch handler remains active.

## Script state and reset
---
All state lives in locals and captured upvalues. When the script is reset (by the object being rezzed, the script being saved, the object being taken into inventory, or an explicit reset), the chunk re-runs from the top and every local is reinitialised. Persisted state must be written somewhere durable before the reset, and read back in the chunk.

```lua
local saved = ll.GetObjectDesc()

local counter = tonumber(saved)
if counter == nil then
    counter = 0
end

LLEvents:on("touch_start", function(events)
    counter += 1
    ll.SetObjectDesc(tostring(counter))
    print("count is now", counter)
end)
```

**Breakdown**

- `ll.GetObjectDesc()` reads the object's description on chunk start.
- `tonumber(saved)` converts the string back to a number; `nil` when the description is empty or not a number.
- If the read fails, `counter` starts at `0`.
- The handler writes the new value back to the description, so it survives the next reset.
- Anything not persisted is lost on reset; this is the source of the classic "my script forgot its state" bug.
