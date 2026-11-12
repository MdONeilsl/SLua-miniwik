# `ll.Target`

```lua
ll.Target(position: vector, range: number) -> number
```

Sets up a target location at the specified position, allowing a configurable tolerance radius. When an object enters or exits this area, it fires at_target and not_at_target events respectively. The function returns an integer identifier that can be used with ll.TargetRemove to delete the target.


## Arguments

| Name | Type | Description |
|---|---|---|
| `position` | `vector` | Target position vector in region coordinates. |
| `range` | `number` | Radius tolerance in meters surrounding the target position. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement` |
