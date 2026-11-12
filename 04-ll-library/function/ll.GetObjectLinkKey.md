# `ll.GetObjectLinkKey`

```lua
ll.GetObjectLinkKey(object_id: uuid, link: number) -> uuid
```

For a given object identified by its UUID, this function retrieves the UUID of the child prim associated with the specified link number within that linkset.

## Arguments

| Name | Type | Description |
|---|---|---|
| `object_id` | `uuid` | UUID of the target prim or linkset. |
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag of the prim to retrieve. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
energy | 10.0 |
sleep | 0.0 |
categories | object, uuid |
