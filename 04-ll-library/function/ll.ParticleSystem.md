# `ll.ParticleSystem`

```lua
ll.ParticleSystem(rules: list | ParticleParams) -> ()
```

This function configures or replaces a particle system on the prim hosting the script, using the specified rules. Passing an empty list will clear the particle system.


## Arguments

| Name | Type | Description |
|---|---|---|
| `rules` | `list | ParticleParams` | A list of particle system rules and data pairs [rule1, data1, ...]. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `effects`, `particles` |
