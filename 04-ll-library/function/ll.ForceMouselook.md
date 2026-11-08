# `ll.ForceMouselook`

```lua
ll.ForceMouselook(mouselook: boolean | number) -> ()
```

When an avatar is seated on this prim, this function determines if they are compelled to use mouselook. Passing TRUE enforces mouselook; passing FALSE (the default) lets the avatar retain their existing camera perspective.


## Arguments

| Name | Type | Description |
|---|---|---|
| `mouselook` | `boolean | number` | Boolean. If TRUE, forces a sitting avatar into mouselook; if FALSE, allows them to keep their current camera mode. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `camera`, `permissions` |