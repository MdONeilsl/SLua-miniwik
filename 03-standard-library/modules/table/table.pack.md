# `table.pack`

```lua
table.pack(...) -> { n: number, [number]: V }
```

Packs all provided arguments into a table, with an `n` field indicating the count, safely handling nils in vararg sequences.

## Arguments

| Name | Type | Description |
|---|---|---|
| `...` | `...V` | Values to include in the packed table. |

**Returns:** `{ n: number, [number]: V }`
