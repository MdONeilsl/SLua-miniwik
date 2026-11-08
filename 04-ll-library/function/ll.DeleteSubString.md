# `ll.DeleteSubString`

```lua
ll.DeleteSubString(src: string, start_index: number, end_index: number) -> string
```

This function creates a new string by removing the substring from start_index to end_index, inclusive. Negative indices are interpreted as positions counting backward from the end. When start_index exceeds end_index, the operation does not delete the specified range.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Source string to modify. |
| `start_index` | `number` | Starting codepoint index of the substring to remove (inclusive). Supports negative indexing. |
| `end_index` | `number` | Ending codepoint index of the substring to remove (inclusive). Supports negative indexing. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `string` |