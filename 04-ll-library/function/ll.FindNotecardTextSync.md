# `ll.FindNotecardTextSync`

```lua
ll.FindNotecardTextSync(name: string | uuid, pattern: string, start: number, count: number, options: list) -> {any}
```

Performs a synchronous search within the region’s cache for occurrences of the specified pattern in the given notecard, without triggering a dataserver event. Returns a list of match positions in the format [line, column, length, ...], one entry per match; returns NAK if the notecard is not cached, or an empty list if no matches are found.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string | uuid` | Name of the notecard in the prim's inventory, or a UUID., type: string, asset-semantics: True |
| `pattern` | `string` | Regular expression pattern to search for. |
| `start` | `number` | Index of the first match to return. |
| `count` | `number` | Maximum number of matches to return (if 0, returns the first 64 matches). |
| `options` | `list` | A list of options to control the search (currently unused, should be []). |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `notecard` |
