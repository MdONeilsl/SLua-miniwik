# `ll.LinkSitTarget`

```lua
ll.LinkSitTarget(link: number, offset: vector, rot: quaternion) -> ()
```

Defines the sit target location and orientation for the specified linked prim, expressed in the prim's local coordinate system. To clear the target, set the offset to <0.0, 0.0, 0.0>.

## Arguments

| Name | Type | Description |
|---|---|---|
| link | number | Link number (1 for root, >1 for children) or a LINK_* flag. |
| offset | vector | Offset position vector in local prim coordinates. |
| rot | quaternion | Rotation relative to the prim's rotation. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `linkset`, `sit` |