# `ll.ParseString2List`

```lua
ll.ParseString2List(src: string, separators: {string}, spacers: {string}) -> {string}
```

Splits the input string `src` into a list of non-empty substrings, removing any characters specified in the `separators` list while retaining those in the `spacers` list, and excluding any resulting empty entries. Both `separators` and `spacers` parameters may contain up to eight string values each.

## Arguments

| Name | Type | Description |
|---|---|---|
| src | string | Source string to parse. |
| separators | {string} | A list of up to 8 strings representing separators to be discarded. |
| spacers | {string} | A list of up to 8 strings representing spacers to be preserved in the list. |

**Returns:** `{string}`

## Definition fields

| Field | Value |
|---|---|
| energy | `10.0` |
| sleep | `0.0` |
| categories | `data_conversion` |