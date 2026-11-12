# `__metatable`

```lua
__metatable: any
```

The presence of this field acts as a safeguard for an object's metatable. If defined, retrieving it using `getmetatable()` returns its stored value, and attempting to change it with `setmetatable()` will cause the operation to fail.

**Type:** `any`
