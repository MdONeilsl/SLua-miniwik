# `bit32.s32`

```lua
bit32.s32(val: number) -> number
```

This function converts a value, taking it from its standard floating-point representation and forcing it into a signed 32-bit integer format by truncating any fractional components. This process ensures that subsequent integer calculations behave correctly within the LSua system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The numerical value intended for truncation. |

**Returns:** `number`
