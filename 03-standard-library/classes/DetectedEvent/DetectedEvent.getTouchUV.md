# `DetectedEvent.getTouchUV`

```lua
DetectedEvent.getTouchUV() -> vector
```

This method returns the UV texture coordinates (<u, v, 0.0>) at the point where the prim was touched; the X and Y components represent the horizontal and vertical texture coordinates, usually ranging from [0.0, 1.0]. If the coordinates cannot be determined, it returns TOUCH_INVALID_TEXCOORD.

**Returns:** `vector`
