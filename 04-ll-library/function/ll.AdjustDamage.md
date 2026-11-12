# `ll.AdjustDamage`

```lua
ll.AdjustDamage(number: number, new_damage: number) -> ()
```

Alters the damage value that will be applied following the completion of the current on_damage event, based on the provided damage event index.


## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | `number` | Index of the damage event to modify. |
| `new_damage` | `number` | New damage value to be applied or distributed after on_damage processing. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `combat`, `detected` |
