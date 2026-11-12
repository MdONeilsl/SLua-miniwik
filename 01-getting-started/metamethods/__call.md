# `__call`

```lua
__call<A..., R...>(self: {}, ...) -> R...
```

When an object or table is invoked using function call syntax, this metamethod determines the result of that invocation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | The table instance receiving the function call. |
| `...` | `A...` | All remaining arguments provided during invocation. |

**Returns:** `R...`
