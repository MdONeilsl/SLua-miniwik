# `os.clock`

```lua
os.clock() -> number
```

Retrieves a highly accurate time measurement, expressed in seconds, suitable for timing elapsed intervals. This value possesses a 0.0001s resolution derived from server and script execution cycles, though accessing it is notably slower than using `ll.GetTime`.

**Returns:** `number`