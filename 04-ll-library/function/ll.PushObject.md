# `ll.PushObject`

```lua
ll.PushObject(target: uuid, impulse: vector, ang_impulse: vector, is_local: boolean | number) -> ()
```

This function imparts a linear force and rotational force to a designated avatar or object within the same region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `uuid` | UUID of the target avatar or object in the same region. |
| `impulse` | `vector` | Linear impulse vector representing the direction and force of the push. |
| `ang_impulse` | `vector` | Angular impulse vector representing the rotational force. |
| `is_local` | `boolean | number` | Boolean. If TRUE, forces are applied relative to the target's local axes; if FALSE, relative to region axes. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `movement`, `physics` |