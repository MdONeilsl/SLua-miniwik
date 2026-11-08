# `buffer.create`

```lua
buffer.create(size: number) -> buffer
```

This function allocates and returns a new buffer object. The resulting memory block will have the specified dimensions and every byte set to zero.

## Arguments

| Name | Type | Description |
|---|---|---|
| `size` | `number` | The desired capacity or length for the new buffer. |

**Returns:** `buffer`