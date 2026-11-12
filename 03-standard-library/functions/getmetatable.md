# `getmetatable`

```lua
getmetatable(obj: T) -> getmetatable<T>
```

Retrieves the metadata associated with a given object. If that metadata contains a field named '__metatable', the function returns the value of that field instead.

## Arguments

| Name | Type | Description |
|---|---|---|
| `obj` | `T` | The object whose internal metadata should be accessed. |

**Returns:** `getmetatable<T>`
