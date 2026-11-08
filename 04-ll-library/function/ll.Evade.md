# `ll.Evade`

```lua
ll.Evade(target: uuid, options: list) -> ()
```

Causes a pathfinding character to attempt to avoid the specified target by seeking a hiding position, provided such a spot exists — specifically, one where there is no direct line of sight from the character’s head to the target’s head and no navigable path on the navmesh connects them.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the group, avatar, or object to evade. |
| `options` | `list` | No options currently available (should be empty list). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |