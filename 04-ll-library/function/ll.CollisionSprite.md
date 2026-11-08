# `ll.CollisionSprite`

```lua
ll.CollisionSprite(impact_sprite: string | uuid) -> ()
```

Disables the default collision sprites and substitutes them with the specified impact_sprite, which must be present in the prim’s inventory. Use an empty string to disable sprites without replacing them.


## Arguments

| Name | Type | Description |
|---|---|---|
| `impact_sprite` | `string | uuid` | UUID of a texture, the name of a texture in the prim's inventory, or an empty string to suppress sprites. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `effects`, `sound` |