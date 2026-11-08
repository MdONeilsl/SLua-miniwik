# `ll.GetMass`

```lua
ll.GetMass() -> number
```

This function returns the mass of the object as a floating-point value, measured in lindograms. When invoked from the root prim, it returns the combined mass of the entire linkset. If called from a child prim, it returns the mass of that specific prim. If the function is called while inside an attachment, it returns the mass of the wearer.

## Arguments

_No arguments._

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `physics` |