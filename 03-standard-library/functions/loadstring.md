# `loadstring`

```lua
loadstring(src: string, chunkname: string?) -> (((A...) -> any)?, string?)
```

This utility compiles provided Lua source code text into an executable function object.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | The source text that needs compilation. |
| `chunkname` | `string?` | An optional identifier for the loaded code segment. |

**Returns:** `(((A...) -> any)?, string?)`