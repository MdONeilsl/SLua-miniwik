# `__newindex`

```lua
__newindex(self: {}, key: any, value: any) -> ()
```

When a value is written to a non-existent key within the table, this metamethod executes. It also serves as a function fallback for such assignments, or can be used generally to forward new key/value creations in a dictionary-like fashion.

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | The table object receiving the assignment operation. |
| `key` | `any` | The identifier used for setting a new key-value pair. |
| `value` | `any` | The data value intended to be set at the specified key. |

**Returns:** `()`
