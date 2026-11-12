# `ll.ParseStringKeepNulls`

```lua
ll.ParseStringKeepNulls(src: string, separators: {string}, spacers: {string}) -> {string}
```

Splits the input string `src` into an array of substrings, omitting the specified separators while retaining the specified spacers, and retains empty entries (in contrast to `ll.ParseString2List`). Both `separators` and `spacers` parameters can contain up to eight string values each.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Source string to parse. |
| `separators` | `{string}` | A list of up to 8 strings representing separators to be discarded. |
| `spacers` | `{string}` | A list of up to 8 strings representing spacers to be preserved in the list. |

**Returns:** `{string}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_conversion` |
