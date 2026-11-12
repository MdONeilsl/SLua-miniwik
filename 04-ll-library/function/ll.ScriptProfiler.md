# `ll.ScriptProfiler`

```lua
ll.ScriptProfiler(flags: number) -> ()
```

Sets the profiling state of the script via specified flags, such as PROFILE_SCRIPT_MEMORY on Mono or PROFILE_NONE. When profiling is active, script performance may be noticeably degraded.


## Arguments

| Name | Type | Description |
|---|---|---|
| `flags` | `number` | PROFILE_* flag (such as PROFILE_NONE or PROFILE_SCRIPT_MEMORY) to set the profiling state. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `script` |
