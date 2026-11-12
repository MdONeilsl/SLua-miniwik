# `debug.info`

```lua
debug.info(co: thread | ((...any) -> ...any) | number, level: number, s: string) -> ...any
```

Retrieves details regarding a callable object or call stack segment using a specified formatting definition.

## Arguments

| Name | Type | Description |
|---|---|---|
| `co` | `thread | ((...any) -> ...any) | number` | A callable object or thread handle, if provided. |
| `level` | `number?` | Specifies a call stack depth or callable entity to examine. |
| `s` | `string` | The text detailing the required debug output format. |

**Returns:** `...any`
