# `table.unpack`

```lua
table.unpack(a: {V}, i: number?, j: number?) -> ...V
```

Extracts elements from the array as individual return values, starting at index `i` and ending at index `j`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `{V}` | Array containing elements to extract. |
| `i` | `number?` | Index where extraction begins. |
| `j` | `number?` | Index where extraction ends (inclusive). |

**Returns:** `...V`
