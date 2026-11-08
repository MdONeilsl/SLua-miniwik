# `ll.SetPhysicsMaterial`

```lua
ll.SetPhysicsMaterial(mask: number, gravity_multiplier: number, restitution: number, friction: number, density: number) -> ()
```

Sets the physical properties of an object based on a bitmask that determines which of the provided float values—gravity multiplier, restitution, friction, or density—will be applied.

## Arguments

| Name | Type | Description |
|---|---|---|
| `mask` | `number` | Bitwise mask combination specifying which of the floats (DENSITY, FRICTION, RESTITUTION, or GRAVITY_MULTIPLIER) to apply. |
| `gravity_multiplier` | `number` | Gravity multiplier float value (range [-1.0, +28.0], default is 1.0). |
| `restitution` | `number` | Elasticity restitution float value (range [0.0, 1.0]). |
| `friction` | `number` | Friction coefficient float value (range [0.0, 255.0]). |
| `density` | `number` | Density float value in kg/m³ (range [1.0, 22587.0]). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `physics`, `prim`, `prim_properties` |