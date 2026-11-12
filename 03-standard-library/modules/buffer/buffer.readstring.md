# `buffer.readstring`

```lua
buffer.readstring(b: buffer, offset: number, count: number) -> string
```

This function extracts a string from the provided buffer object. The extraction starts at the specified byte offset and continues for the requested quantity of bytes.

## Arguments

| Name | Type | Description |
|---|---|---|
| `b` | `buffer` | Buffer object used as the source data container. |
| `offset` | `number` | Starting index, measured in zero-based bytes. |
| `count` | `number` | The total count of consecutive bytes to retrieve. |

**Returns:** `string`
