# `lljson.slencode`

```lua
lljson.slencode(value: any, options: LLJsonEncodeOptions?) -> string
```

Encodes a Lua value into SL-typed JSON format, supporting custom formatting via optional settings. Throws an error if the input contains unsupported data types.

## Arguments

| Name | Type | Description |
|---|---|---|
| `value` | `any` | Input data to convert into SL-compatible JSON representation. |
| `options` | `LLJsonEncodeOptions?` | Configuration object to fine-tune output formatting behavior. |

**Returns:** `string`