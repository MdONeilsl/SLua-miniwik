# `ll.GetBoundingBox`

```lua
ll.GetBoundingBox(object: uuid) -> {vector}
```

Returns the bounding box for the specified object, encompassing all linked prims, expressed in local coordinates relative to the root prim, in the format [ (vector) min_corner, (vector) max_corner ].


## Arguments

| Name | Type | Description |
|---|---|---|
| `object` | `uuid` | UUID of the avatar or prim in the same region. |

**Returns:** `{vector}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `object` |
