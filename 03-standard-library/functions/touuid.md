# `touuid`

```lua
touuid(val: string? | buffer | uuid) -> uuid?
```

The function constructs a unique identifier (UUID) using provided data that can be an existing UUID, a text string, or raw binary data. It will return nil if the supplied string lacks proper formatting or if the buffer size is less than 16 bytes.

## Arguments

| Name | Type | Description |
|---|---|---|
| `val` | `string? | buffer | uuid` | Input that can be converted into a unique identifier, such as text or raw bytes. |

**Returns:** `uuid?`