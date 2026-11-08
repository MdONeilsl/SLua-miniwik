# `rawlen`

```lua
rawlen(t: {[K]: V} | string) -> number
```

This function determines the size (length) of either a given string or table by ignoring any custom length determination methods defined via `__len`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `t` | `{[K]: V} | string` | The data structure, which can be a table or a string, whose size is desired. |

**Returns:** `number`