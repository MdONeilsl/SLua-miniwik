# `bit32.rrotate`

```lua
bit32.rrotate(val: number, i: number) -> number
```

This function rotates the value `val` to the right by the amount specified in `i`. Should `i` be negative, the operation defaults to performing a left rotation instead.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The integer value that will undergo rotation. |
| `i` | `number` | The count of bit positions used for rotation. |

**Returns:** `number`
