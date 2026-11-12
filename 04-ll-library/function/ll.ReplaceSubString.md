# `ll.ReplaceSubString`

```lua
ll.ReplaceSubString(src: string, pattern: string, replacement_pattern: string, count: number) -> string
```

This function creates a new string by replacing up to count instances of pattern in src with replacement_pattern. When count is zero, all matches are substituted; for positive values, replacements occur from left to right, and for negative values, they proceed from right to left.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Original source string to search. |
| `pattern` | `string` | Substring pattern to find and replace. |
| `replacement_pattern` | `string` | New substring that replaces the pattern. |
| `count` | `number` | Maximum number of replacements to make (0 for all, positive for left-to-right, negative for right-to-left). |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `string` |
