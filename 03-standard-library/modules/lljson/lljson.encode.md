# `lljson.encode`

```lua
lljson.encode(value: any, options: LLJsonEncodeOptions?) -> string
```

Converts a Lua value into its JSON string representation, throwing an error if the value includes unsupported types.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `any` | Value to be converted into JSON-compatible text. |
| `options` | `LLJsonEncodeOptions?` | Optional settings to control output format or override serialization behavior. |

**Returns:** `string`
