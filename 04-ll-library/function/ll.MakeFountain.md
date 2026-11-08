# `ll.MakeFountain`

```lua
ll.MakeFountain(particles: number, scale: number, vel: number, lifetime: number, arc: number, bounce: number, texture: string | uuid, offset: vector, bounce_offset: number) -> ()
```

This function is obsolete and creates a particle fountain effect. Replace it with ll.ParticleSystem.

## Arguments

| Name | Type | Description |
|---|---|---|
| `particles` | `number` | — |
| `scale` | `number` | — |
| `vel` | `number` | — |
| `lifetime` | `number` | — |
| `arc` | `number` | — |
| `bounce` | `number` | — |
| `texture` | `string | uuid` | Name of a texture in the prim's inventory, or a UUID. |
| `offset` | `vector` | Offset relative to the prim's position (expressed in local coordinates; completely ignored by the system). |
| `bounce_offset` | `number` | — |

**Returns:** `()`

## Deprecated

- **use:** ll.ParticleSystem

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.1` |
| `categories` | `effects` |