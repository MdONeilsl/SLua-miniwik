# `string.split`

```lua
string.split(src: string, separator: string?) -> {string}
```

This function divides a given string using a specified separator, returning an array of resulting substrings. If no separator is provided (`nil`), commas are used as delimiters; otherwise, an empty separator splits the source into individual bytes.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | The input text that needs to be divided. |
| `separator` | `string?` | Specifies the dividing character. Uses commas if omitted, or individual bytes if empty. |

**Returns:** `{string}`