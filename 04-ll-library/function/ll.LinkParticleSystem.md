# `ll.LinkParticleSystem`

```lua
ll.LinkParticleSystem(link: number, rules: list | ParticleParams) -> ()
```

Sets up or modifies a particle system on the specified linked prim, using the provided rules. Passing an empty list will clear the particle system.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `rules` | `list | ParticleParams` | A list of particle system rules and data pairs [rule1, data1, ...], or a ParticleParams dictionary. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `effects`, `particles` |
