# `ll.GetParcelPrimOwners`

```lua
ll.GetParcelPrimOwners(pos: vector) -> {any}
```

This function retrieves a list of up to 100 ownership entries, each in the form [key owner, integer land_impact], for objects located on the parcel at the specified position. The results are ordered by the owner's key. It necessitates owner-level permissions for the parcel and the script owner must be present within the region.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `2.0` |
| `categories` | `parcel` |