# `string.match`

```lua
string.match(src: string, pattern: string, start_index: number?) -> ...string?
```

This function finds all instances matching the specified regular expression within the source text. Searching begins at `start_index`, and if no match exists, it returns nil.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | The textual content that will be analyzed for matches. |
| `pattern` | `string` | The regular expression defining what sequence of characters must be matched. |
| `start_index` | `number?` | Byte position where searching should begin; defaults to 1, but accepts negative values. |

**Returns:** `...string?`
