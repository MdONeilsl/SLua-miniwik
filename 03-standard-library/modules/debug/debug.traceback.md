# `debug.traceback`

```lua
debug.traceback(co: thread, msg: string?, level: number?) -> string
```

This function generates a readable representation of the program's calling sequence. The resulting stack trace can be restricted to start at a specific depth within the call history.

## Arguments

| Name | Type | Description |
|---|---|---|
| `co` | `thread?` | An optional pointer to the execution thread being examined. |
| `msg` | `string?` | Any text that will appear before the stack trace output. |
| `level` | `number?` | Specifies the depth at which the stack trace should begin. |

**Returns:** `string`