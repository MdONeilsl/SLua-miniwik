# `VEHICLE_BANKING_EFFICIENCY`

This float value, which ranges from -1.0 to 1.0, governs how banking affects efficiency. Specifically, negative input values cause a lean away from the turn, while positive values result in leaning into the curve. Setting this parameter makes steering sensitive to banking; consequently, angular motors must be employed for banking effects. A value of 0.0 indicates that no banking effect is present.

**Type:** `number`

**Value:** `38`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `VehicleFloatParam` |