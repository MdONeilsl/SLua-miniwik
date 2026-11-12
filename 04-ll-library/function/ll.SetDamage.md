# `ll.SetDamage`

```lua
ll.SetDamage(damage: number) -> ()
```

When this object collides with an avatar, it applies the specified damage amount and then instantly deletes itself, without generating any collision event.


## Arguments

| Name | Type | Description |
|---|---|---|
| `damage` | `number` | Float damage value to set (range -100.0 for full heal to 100.0 for instant kill). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `combat` |
