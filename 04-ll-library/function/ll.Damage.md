# `ll.Damage`

```lua
ll.Damage(target: uuid, damage: number, damage_type: number) -> ()
```

Triggers a damage event that applies the given damage value and damage type to the specified target avatar or task within the same region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | Key of the target avatar or task to receive damage. |
| `damage` | `number` | Amount of damage to inflict (can exceed 100, unlike collision-based damage). |
| `damage_type` | `number` | Type of damage to deliver to the target (can correspond to a DAMAGE_TYPE_* constant). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `combat` |