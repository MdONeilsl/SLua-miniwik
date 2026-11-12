# `tonumber`

```lua
tonumber(value: string? | number, base: number?) -> number?
```

This function attempts to convert the provided value into a numerical type using a specified radix (base). If the conversion fails due to invalid input, it will return nil.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `string? | number` | The string that needs converting into a numeric value. |
| `base` | `number?` | The radix used for conversion; must fall within the range [2, 36]. |

**Returns:** `number?`
