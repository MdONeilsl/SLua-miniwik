# `ll.SetRot`

```lua
ll.SetRot(rot: quaternion) -> ()
```

Assigns the specified rotation to the prim. When called from a child prim, the rotation is interpreted relative to the root prim; when invoked from the root prim of a non-physical object, it affects the entire object’s orientation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `rot` | `quaternion` | Target rotation. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `movement`, `prim` |