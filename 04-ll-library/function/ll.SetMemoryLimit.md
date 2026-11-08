# `ll.SetMemoryLimit`

```lua
ll.SetMemoryLimit(limit: number) -> number
```

This function requests that the script reserve a specified amount of memory in bytes. It returns 1 on success or 0 on failure, though it has no effect in LSO.


## Arguments

| Name | Type | Description |
|---|---|---|
| `limit` | `number` | Integer memory limit in bytes to reserve (must be less than the 64KB maximum). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `script` |