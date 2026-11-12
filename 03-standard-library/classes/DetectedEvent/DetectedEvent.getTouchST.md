# `DetectedEvent.getTouchST`

```lua
DetectedEvent.getTouchST() -> vector
```

When a prim is touched, this method returns the surface coordinates in the form (<s, t, 0.0>), where s and t represent the horizontal and vertical positions on the prim’s surface (usually ranging from 0.0 to 1.0). If the coordinates cannot be resolved, it returns TOUCH_INVALID_TEXCOORD.

**Returns:** `vector`
