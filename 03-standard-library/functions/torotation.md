# `torotation`

```lua
torotation(value: string? | quaternion) -> quaternion?
```

Takes a string representation and computes the associated rotation as a quaternion. If conversion fails due to invalid input, it returns `nil`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `string? | quaternion` | Input text that specifies the desired rotation. |

**Returns:** `quaternion?`
