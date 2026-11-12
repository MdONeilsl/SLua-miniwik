# `integer.clamp`

```lua
integer.clamp(val: integer, min: integer, max: integer) -> integer
```

The function adjusts a value so that it falls within the specified range defined by minimum and maximum boundaries. It will throw an exception if the provided minimum value exceeds the maximum value.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `integer` | The integer value that needs constraining. |
| `min` | `integer` | The lowest acceptable whole number boundary. |
| `max` | `integer` | The highest permissible whole number limit. |

**Returns:** `integer`
