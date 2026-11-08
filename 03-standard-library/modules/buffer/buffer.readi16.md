# `buffer.readi16`

```lua
buffer.readi16(b: buffer, offset: number) -> number
```

Extracts a signed 16-bit numerical value stored in the buffer, using the offset to determine its location.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | The source buffer containing data for retrieval. |
| `offset` | `number` | Index indicating the byte location where reading begins. |

**Returns:** `number`