# `string.gmatch`

```lua
string.gmatch(src: string, pattern: string) -> () -> ...string
```

Iterates over all matches of the given pattern within the source string, yielding each match sequentially.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | String to scan for pattern matches. |
| `pattern` | `string` | Regular expression defining what to match. |

**Returns:** `() -> ...string`
