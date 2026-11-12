# `integer.fromstring`

```lua
integer.fromstring(value: string, base: number?) -> integer?
```

Converts a given text representation into an integer using a specified numeral system foundation. If the provided string cannot be interpreted as an integer in that particular base, the function returns nil.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `string` | The textual input that needs conversion into a whole number. |
| `base` | `number?` | The numerical system foundation used during the transformation process. |

**Returns:** `integer?`
