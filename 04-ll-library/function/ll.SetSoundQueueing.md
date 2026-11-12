# `ll.SetSoundQueueing`

```lua
ll.SetSoundQueueing(queue: boolean | number) -> ()
```

Controls whether subsequent sounds will be queued to play only after the current sound finishes. Enabling this (with queue set to TRUE) allows queuing, while disabling it (with queue set to FALSE) prevents it. The queue operates with a single-level depth.


## Arguments

| Name | Type | Description |
|---|---|---|
| `queue` | `boolean | number` | Boolean. If TRUE, sound queuing is enabled; if FALSE, it is disabled. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
