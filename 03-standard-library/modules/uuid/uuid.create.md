# `uuid.create`

```lua
uuid.create(value: string? | buffer | uuid) -> uuid
```

Generates a new UUID instance from a string representation, binary buffer, or existing UUID object; raises an error if the input string is invalid or the buffer is insufficiently long.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `string? | buffer | uuid` | Input source: string, buffer, or UUID to convert |

**Returns:** `uuid`