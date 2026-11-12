# `ll.GenerateKey`

```lua
ll.GenerateKey() -> uuid
```

Produces a unique, versioned UUID key using SHA-1 hashing. Because it is versioned, it will never return NULL_KEY; however, the specific UUID version used is an implementation detail and should not be depended upon.


## Arguments

_No arguments._

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `uuid` |
