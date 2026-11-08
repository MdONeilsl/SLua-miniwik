# `os.date`

```lua
os.date(formatString: string?, t: number?) -> string
```

This function generates a textual representation of a point in time using the given formatting rules.

## Arguments

| Name | Type | Description |
|---|---|---|
| `formatString` | `string?` | Specifies how the resulting date should be formatted. |
| `t` | `number?` | The numerical timestamp used for formatting, or the present moment if omitted. |

**Returns:** `string`