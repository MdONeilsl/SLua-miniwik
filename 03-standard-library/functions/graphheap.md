# `graphheap`

```lua
graphheap(path: string) -> ()
```

Serializes the current heap contents to a file at the given location, ensuring the data adheres to JSON formatting standards. This process is typically used in conjunction with external analysis utilities like graphanalyze.py.

## Arguments

| Name | Type | Description |
|---|---|---|
| `path` | `string` | The required filesystem path where the heap structure will be saved. |

**Returns:** `()`
