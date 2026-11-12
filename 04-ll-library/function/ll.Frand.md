# `ll.Frand`

```lua
ll.Frand(mag: number) -> number
```

Generates a pseudo-random floating-point number within the interval [0.0, mag) if mag is positive, or (mag, 0.0] if mag is negative. The result always includes 0.0 but excludes mag.

## Arguments

| Name | Type | Description |
|---|---|---|
| `mag` | `number` | Float magnitude of the random range. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math` |
