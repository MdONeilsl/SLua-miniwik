# `string.gsub`

```lua
string.gsub(src: string, pattern: string, repl: string | { [string]: string } | (...string) -> string, maxn: number?) -> (string, number)
```

Replaces up to `maxn` occurrences of `pattern` in `src` with `repl`, returning the modified string and the count of replacements made.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Input string to modify by substitution. |
| `pattern` | `string` | Regular expression to locate replacement targets. |
| `repl` | `string | { [string]: string } | (...string) -> string` | Replacement value: string, lookup table, or callable function. |
| `maxn` | `number?` | Limit on how many replacements to perform; unlimited if omitted. |

**Returns:** `(string, number)`
