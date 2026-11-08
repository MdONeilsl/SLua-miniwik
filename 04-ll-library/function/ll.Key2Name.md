# `ll.Key2Name`

```lua
ll.Key2Name(id: uuid) -> string
```

Given a key identifying a prim or avatar within the same region, this function returns the corresponding entity's name as a string. If the target is not a valid, rezzed entity in the current region, it returns an empty string. For avatars, the legacy name is provided.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | uuid | UUID of the target avatar or prim in the same region. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `object` |