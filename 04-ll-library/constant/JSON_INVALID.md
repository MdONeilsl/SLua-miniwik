# `JSON_INVALID`

This constant signals that either the state is incorrect or one of the parameters provided is invalid. It can be returned by `ll.List2Json` if its inputs are improperly formatted, by `ll.JsonValueType` when checking for an unsupported JSON data type, or by `ll.JsonGetValue` if it is called to retrieve a value from a non-existent path.

**Type:** `string`

**Value:** `\u{FDD0}`

## Deprecated

- **use:** pcall