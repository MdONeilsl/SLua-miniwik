# `ll.SetPos`

```lua
ll.SetPos(pos: vector) -> ()
```

Moves the object or prim toward the specified position vector, with a maximum distance of 10 meters. When invoked from a child prim, the position is interpreted relative to the root; when called from the root prim, the entire object is moved.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector to move to (in region coordinates, or local coordinates if in a child prim). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `movement`, `prim` |
