# `ll.GetObjectDetails`

```lua
ll.GetObjectDetails(id: uuid, params: {number}) -> {any}
```

This function retrieves a list of specified attributes for the given avatar or object, ordered according to the parameters provided in the list.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar or prim (in the same or adjacent regions) to query. |
| `params` | `{number}` | A list of OBJECT_* flags specifying the attributes to retrieve. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `object`, `prim_properties` |