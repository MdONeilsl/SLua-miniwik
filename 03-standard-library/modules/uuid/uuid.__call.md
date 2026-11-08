# `uuid.__call`

```lua
uuid(value: string? | buffer | uuid) -> uuid
```

This function generates a unique UUID value using various input types such as strings, buffers, or existing UUID objects. Calling this is equivalent to `uuid.create()`, but it performs strict validation on the provided data formats.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `string? | buffer | uuid` | Input data used to construct a new UUID. |

**Returns:** `uuid`