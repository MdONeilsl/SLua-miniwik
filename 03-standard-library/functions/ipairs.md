# `ipairs`

```lua
ipairs(tab: {V}) -> (({V}, number) -> (number?, V), {V}, number)
```

Iterates over the table’s integer-indexed entries starting at 1, stopping when the first nil value is encountered.

## Arguments

| Name | Type | Description |
|---|---|---|
| `tab` | `{V}` | Table containing sequential integer keys to traverse. |

**Returns:** `(({V}, number) -> (number?, V), {V}, number)`
