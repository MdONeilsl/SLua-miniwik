# `ll.PassTouches`

```lua
ll.PassTouches(pass: number) -> ()
```

Configures the pass-touches behavior: when pass is TRUE, touch events propagate from child prims upward to the root; when FALSE (the default), events are confined to the prim that received the touch.


## Arguments

| Name | Type | Description |
|---|---|---|
| pass | number | A PASS_* flag (e.g., PASS_ALWAYS, PASS_IF_NOT_HANDLED, or PASS_NEVER). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | touch |