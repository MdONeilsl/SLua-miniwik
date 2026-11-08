# `llbase64.decode`

```lua
llbase64.decode(data: string, asBuffer: false?) -> string
```

It converts a base64 encoded sequence into its original format. The result will be text or binary data depending on the provided flag; decoding halts when an error is encountered.

## Arguments

| Name | Type | Description |
|---|---|---|
| `data` | `string` | The input string that uses base64 encoding. |
| `asBuffer` | `false?` | Specifies whether the decoded data should be treated as text or binary. |

**Returns:** `string`