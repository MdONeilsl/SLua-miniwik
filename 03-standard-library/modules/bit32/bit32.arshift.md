# `bit32.arshift`

```lua
bit32.arshift(val: number, i: number) -> number
```

Shifts an integer by i bits with arithmetic behavior for right shifts (positive displacement), and zero-fill for left shifts (negative). The magnitude of the shift determines the result.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The base value undergoing a bitwise operation. |
| `i` | `number` | The displacement parameter controlling direction and extent. |

**Returns:** `number`
