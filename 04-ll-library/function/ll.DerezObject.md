# `ll.DerezObject`

```lua
ll.DerezObject(id: uuid, flags: number) -> boolean
```

Removes or retrieves a specified object from the region that was previously rezzed by a script within this linkset, with the result being either TRUE for success or FALSE for failure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the object in the region to derez. |
| `flags` | `number` | Derez behavior flags matching DEREZ_* constants. |

**Returns:** `boolean`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `prim_inventory`, `rez` |
