# `ll.CollisionFilter`

```lua
ll.CollisionFilter(name: string, id: uuid, accept: boolean | number) -> ()
```

Configures the collision filter to include or exclude collisions based on specified name and ID criteria. When accept is TRUE, only collisions that match both the name and ID are handled; when FALSE, those matching the criteria are ignored. Omitting a filter by passing an empty string or NULL_KEY for either name or ID disables that particular filter condition.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string` | Specific object name or avatar legacy name to filter for. |
| `id` | `uuid` | Group, avatar, or object UUID to filter by. |
| `accept` | `boolean | number` | Boolean. If TRUE, only collisions matching the name and id filters are processed; if FALSE, matching collisions are excluded. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `sensor` |
