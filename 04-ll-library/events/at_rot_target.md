# `at_rot_target`

```lua
at_rot_target(handle: number, targetrot: quaternion, ourrot: quaternion) -> ()
```

The event fires when the object's current orientation approaches the desired rotation that was initially established using `llRotTarget`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `handle` | `number` | The unique integer identifier given when calling `llRotTarget`. |
| `targetrot` | `quaternion` | The desired rotational value set during the `llRotTarget` function call. |
| `ourrot` | `quaternion` | The object's current orientation, similar to what `llGetRot()` returns. |

**Returns:** `()`
