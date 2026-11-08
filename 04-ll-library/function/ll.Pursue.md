# `ll.Pursue`

```lua
ll.Pursue(target: uuid, options: list) -> ()
```

Causes a pathfinding character to actively track and follow the specified target, with behavior fine-tuned through the provided options.


## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the group, avatar, or object to pursue. |
| `options` | `list` | A list of options to configure pursuit behavior. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |