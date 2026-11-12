# `__tojson`

```lua
__tojson(self: {}, ctx: { mode: "json" | "sljson", tight: boolean }) -> any
```

When JSON serialization is executed, this metamethod is invoked. It returns a substitute value that will be used in place of the original table during the encoding process.

## Arguments

| Name | Type | Description |
|---|---|---|
| `self` | `{}` | The table object undergoing the serialization process. |
| `ctx` | `{ mode: "json" | "sljson", tight: boolean }` | Metadata regarding the encoding context, specifying mode and tightness. |

**Returns:** `any`
