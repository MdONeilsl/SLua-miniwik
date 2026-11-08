# `ll.MakeSmoke`

```lua
ll.MakeSmoke(particles: number, scale: number, vel: number, lifetime: number, arc: number, texture: string | uuid, offset: vector) -> ()
```

No longer supported. Creates smoke-effect particles; replace with ll.ParticleSystem.

## Arguments

| Name | Type | Description |
|---|---|---|
| `particles` | `number` | — |
| `scale` | `number` | — |
| `vel` | `number` | — |
| `lifetime` | `number` | — |
| `arc` | `number` | — |
| `texture` | `string | uuid` | Name of a texture in the prim's inventory, or a UUID. |
| `offset` | `vector` | Offset relative to the prim's position (expressed in local coordinates; completely ignored by the system). |

**Returns:** `()`

## Deprecated

- **use:** ll.ParticleSystem

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `effects` |