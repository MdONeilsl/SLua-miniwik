# `graphuserheap`

```lua
graphuserheap(path: string) -> ()
```

This function saves the data contained within the user heap to disk. The resulting file will be formatted using JSON structure, making it suitable for analysis tools.

## Arguments

| Name | Type | Description |
|---|---|---|
| `path` | `string` | The location where the serialized heap contents should be saved. |

**Returns:** `()`
