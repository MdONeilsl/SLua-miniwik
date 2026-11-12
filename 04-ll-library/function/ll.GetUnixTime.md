# `ll.GetUnixTime`

```lua
ll.GetUnixTime() -> number
```

Returns the current Unix timestamp as an integer, which corresponds to the number of seconds that have passed since 00:00:00 UTC on January 1, 1970.

## Arguments

_No arguments._

**Returns:** `number`

## Deprecated

- **use:** os.time
- **reason:** Int32 will wrap on 2038-01-19

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `time` |
