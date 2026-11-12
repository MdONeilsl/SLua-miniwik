# `table.insert`

```lua
table.insert(a: {V}, i: number, value: V) -> ()
```

This function places an item at the specified index, causing all subsequent elements to shift their positions upward by one unit. The target index must be located within the range of 1 up to the current length of the array.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | The table structure where the new element will be added. |
| `i` | `number?` | Specifies the location for insertion; items starting from this point move one position higher. |
| `value` | `V` | The data content that needs to be added into the table. |

**Returns:** `()`
