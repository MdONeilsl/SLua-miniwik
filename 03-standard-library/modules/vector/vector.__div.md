# `vector.__div`

```lua
vector.__div(self: vector, other: number | vector | quaternion) -> vector
```

This method handles division operations. Dividing by a scalar number scales the vector, while dividing by a quaternion applies an inverse rotation transformation.

## Arguments

| Name | Type | Description |
|---|---|---|
| `other` | `number | vector | quaternion` | The value used as the divisor in the operation. |

**Returns:** `vector`
