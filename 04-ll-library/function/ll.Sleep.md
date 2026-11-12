# `ll.Sleep`

```lua
ll.Sleep(sec: number) -> ()
```

Suspends the script for sec seconds, pausing execution until the next server frame (approximately 0.02222 seconds). The script remains inactive during this pause. If sec is 0.0 or lower, no suspension occurs.


## Arguments

| Name | Type | Description |
|---|---|---|
| `sec` | number | Duration in seconds to put the script to sleep. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `0.0` |
| `sleep` | `0.0` |
| `categories` | `script`, `time` |
