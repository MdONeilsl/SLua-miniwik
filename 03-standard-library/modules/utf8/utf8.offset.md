# `utf8.offset`

```lua
utf8.offset(str: string, n: number, start_index: number?) -> number?
```

Returns the byte position where the nth Unicode character begins, counting from the start or end depending on sign of n. If start_index is provided, counting begins there instead of at the string’s start.

## Arguments

| Name | Type | Description |
|---|---|---|
| `str` | `string` | String to search within. |
| `n` | `number` | Target character position; negative values count from the end. |
| `start_index` | `number?` | Byte offset to begin counting from; defaults to 1 if not given. |

**Returns:** `number?`
