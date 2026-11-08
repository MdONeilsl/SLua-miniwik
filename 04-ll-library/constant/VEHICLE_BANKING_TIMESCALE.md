# `VEHICLE_BANKING_TIMESCALE`

A floating-point parameter for `Vehicle` that dictates the exponential timescale required for the implemented banking behavior to reach its full effect. Functionally, this serves as an alternative method for adjusting the overall strength of the banking effect; specifically, it modulates the term derived from the discrepancy between the intended banking movement and the vehicle's current actual motion.

**Type:** `number`

**Value:** `40`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `VehicleFloatParam` |