# `integer.lrotate`

```lua
integer.lrotate(val: integer, i: integer) -> integer
```

The function shifts `val` by `i` positions to the left circularly. When `i` holds a negative value, this operation executes as a right rotation instead.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `integer` | The integer value that will undergo rotation. |
| `i` | `integer` | The quantity determining the shift amount in bits. |

**Returns:** `integer`