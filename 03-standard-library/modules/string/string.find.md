# `string.find`

```lua
string.find(src: string, pattern: string, start_index: number?, plain: boolean?) -> (number?, number?, ...string)
```

The function locates the first match of a pattern within a string and returns its byte range and any captured groups, or nil if no match exists. It begins searching at a specified position, defaulting to the start of the string.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | String to examine for pattern matches. |
| `pattern` | `string` | Sequence or regex to locate within the source. |
| `start_index` | `number?` | Position to begin searching; defaults to 1, supports negative offsets. |
| `plain` | `boolean?` | If true, disables pattern interpretation and matches exactly. |

**Returns:** `(number?, number?, ...string)`
