# `ll.GetSubString`

```lua
ll.GetSubString(src: string, start_index: number, end_index: number) -> string
```

Extracts a substring from the given source string, encompassing codepoints from start_index through end_index, inclusive. Negative indices are interpreted as offsets from the end of the string. When start_index exceeds end_index, the result is the reverse range, excluding the specified bounds.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Source string to slice. |
| `start_index` | `number` | Starting codepoint index (inclusive). Supports negative indexing. |
| `end_index` | `number` | Ending codepoint index (inclusive). Supports negative indexing. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
energy | `10.0` |
sleep | `0.0` |
categories | `string` |
