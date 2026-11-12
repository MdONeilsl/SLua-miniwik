# `lljson.sldecode`

```lua
lljson.sldecode(json: string, options: LLJsonDecodeOptions?) -> any
```

Decodes a JSON string into a Lua value, maintaining SL-specific data types. Throws an error if the input JSON is malformed.

## Arguments

| Name | Type | Description |
|---|---|---|
| `json` | `string` | Input JSON string encoded with SL type conventions. |
| `options` | `LLJsonDecodeOptions?` | Configuration object to customize parsing behavior, if provided. |

**Returns:** `any`
