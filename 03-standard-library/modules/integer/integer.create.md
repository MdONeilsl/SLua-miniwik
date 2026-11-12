# `integer.create`

```lua
integer.create(val: number) -> integer?
```

The function attempts to convert the provided numeric value into an integer. Conversion fails and returns nil if the number has fractional components, falls outside valid ranges, or represents NaN.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `number` | The numerical input used to generate the integer representation. |

**Returns:** `integer?`
