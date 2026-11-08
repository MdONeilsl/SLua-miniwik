# `vector.__mul`

```lua
vector.__mul(self: vector, other: number | vector | quaternion) -> vector
```

This operation handles multiplication, resulting in scaling when multiplying two vectors, or performing rotations when multiplied by a quaternion.

## Arguments

| Name | Type | Description |
|---|---|---|
| `other` | `number | vector | quaternion` | The operand used to scale, rotate, or multiply the vector. |

**Returns:** `vector`