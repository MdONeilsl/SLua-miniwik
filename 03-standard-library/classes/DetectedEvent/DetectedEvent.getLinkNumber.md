# `DetectedEvent.getLinkNumber`

```lua
DetectedEvent.getLinkNumber() -> number
```

Returns the link number of the detected entity. Unlinked objects yield 0, the root prim yields 1, and child prims yield 2 or higher; events without link-number support also return 0.

**Returns:** `number`
