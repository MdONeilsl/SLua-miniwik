# `table.remove`

```lua
table.remove(a: {V}, i: number?) -> V?
```

Removes and returns the item located at a specified index, causing all following elements to shift down by one position. If no element is deleted, the function will return nil.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | The table structure from which an element must be removed. |
| `i` | `number?` | Position of the item to delete; subsequent elements adjust downwards. |

**Returns:** `V?`