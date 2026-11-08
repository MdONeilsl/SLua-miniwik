# `ll.GetNotecardLineSync`

```lua
ll.GetNotecardLineSync(name: string | uuid, line: number) -> string
```

Reads the specified line from a notecard stored in the prim's inventory or identified by UUID, using the region’s cache without triggering a dataserver event. Returns "NAK" if the notecard is not cached, or "EOF" if the requested line exceeds the notecard’s content.

## Arguments

| Name | Type | Description |
|---|---|---|
| `name` | `string | uuid` | — |
| `line` | `number` | Index of the line to read. |

**Returns:** `string`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `notecard` |