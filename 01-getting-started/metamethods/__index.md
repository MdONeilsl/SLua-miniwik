# `__index`

```lua
__index(self: {}, key: any) -> any
```

When a program attempts to retrieve a non-existent key from the table, this metamethod dictates the return value. It can be invoked as a function fallback or used directly as a lookup dictionary for missing entries, providing a mechanism to locate data that is otherwise unavailable.

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | The table from which the key lookup is being performed. |
| `key` | `any` | The specific key requested that does not exist within the associated table. |

**Returns:** `any`
