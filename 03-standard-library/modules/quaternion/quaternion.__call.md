# `quaternion.__call`

```lua
quaternion(x: number, y: number, z: number, s: number) -> quaternion
```

Calling this function generates a new quaternion instance using the provided component values. This method serves as an alternative way to call `quaternion.create()`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `x` | `number` | The X axis value for the rotation. |
| `y` | `number` | The Y axis value for the rotation. |
| `z` | `number` | The Z axis value for the rotation. |
| `s` | `number` | The scalar magnitude component. |

**Returns:** `quaternion`