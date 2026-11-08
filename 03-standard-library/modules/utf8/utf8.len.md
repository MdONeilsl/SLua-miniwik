# `utf8.len`

```lua
utf8.len(str: string, start_index: number?, end_index: number?) -> (number?, number?)
```

The function calculates how many Unicode codepoints exist within a specified byte range (inclusive) of the source string. Should the provided string not be valid UTF-8, the return value will indicate an error pair instead.

## Arguments

| Name | Type | Description |
|---|---|---|
| `str` | `string` | The input text whose codepoints are being counted. |
| `start_index` | `number?` | Beginning byte position (inclusive); defaults to 1, accepting negative values. |
| `end_index` | `number?` | Ending byte position (inclusive); defaults to the string length, accepting negative values. |

**Returns:** `(number?, number?)`