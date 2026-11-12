# `tostring`

```lua
tostring(value: T) -> string
```

The function transforms any given input value into its string representation. If the object has a defined metatable, it will invoke the `__tostring` metamethod found there.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `T` | Input object requiring string representation. |

**Returns:** `string`
