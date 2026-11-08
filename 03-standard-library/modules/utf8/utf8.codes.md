# `utf8.codes`

```lua
utf8.codes(src: string) -> ((string, number) -> (number, number), string, number)
```

Each character in the input string is processed to yield its byte position and corresponding Unicode codepoint, via an iterator function.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `string` | Input text to iterate over character by character. |

**Returns:** `((string, number) -> (number, number), string, number)`