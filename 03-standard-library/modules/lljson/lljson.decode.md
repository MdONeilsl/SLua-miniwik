# `lljson.decode`

```lua
lljson.decode(json: string, options: LLJsonDecodeOptions?) -> any
```

Converts a JSON-formatted string into a corresponding Lua data structure. If the input is malformed, the function raises an error.

## Arguments

| Name | Type | Description |
|---|---|---|
| `json` | `string` | Input JSON text to convert into a Lua value. |
| `options` | `LLJsonDecodeOptions?` | Optional settings or custom reviver to modify parsing behavior. |

**Returns:** `any`
