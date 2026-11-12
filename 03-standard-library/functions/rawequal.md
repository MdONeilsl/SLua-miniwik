# `rawequal`

```lua
rawequal(a: T1, b: T2) -> boolean
```

Determines if both inputs share matching types and values, including checking references directly without invoking any custom comparison logic.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `T1` | The primary object that will undergo checking. |
| `b` | `T2` | The secondary object used in the equality check. |

**Returns:** `boolean`
