# `error`

```lua
error(message: T, level: number?) -> never
```

Initiates an exception using the provided data. An optional parameter allows specifying which depth within the execution stack is responsible for the failure.

## Arguments

| Name | Type | Description |
|---|---|---|
| `message` | `T` | The content of the error, which may be any object or message. |
| `level` | `number?` | Depth in the calling sequence attributed to the failure (1 is current, 2 is caller). |

**Returns:** `never`
