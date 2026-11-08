# `assert`

```lua
assert(value: T?, errorMessage: string?) -> T
```

Verifies if a given input value evaluates to true; otherwise, it throws an error that can include custom text. If validation passes, the function returns the original value.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `T?` | The item whose truth status needs verification. |
| `errorMessage` | `string?` | Optional text shown when the input fails validation. |

**Returns:** `T`