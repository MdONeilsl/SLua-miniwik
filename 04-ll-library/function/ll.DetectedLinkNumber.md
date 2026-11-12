# `ll.DetectedLinkNumber`

```lua
ll.DetectedLinkNumber(number: number) -> number
```

For touch and collision events, this function returns the integer link number corresponding to the specified detection index. Unlinked objects return 0, the root prim returns 1, and child prims return values of 2 or higher. It returns 0 if the event does not support link number retrieval.


## Arguments

| Name | Type | Description |
|---|---|---|
| `number` | `number` | Index of the detection information. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `detected` |
