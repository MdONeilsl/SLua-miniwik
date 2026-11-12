# `DAMAGEABLE`

This constant flags any object within the simulated environment that has the capability to receive and process damage. When used in `ll.DetectedType`, this value signifies either a physical agent capable of taking damage or an object equipped with a script that utilizes the `on_damage` or `final_damage` events. Furthermore, it can be employed to restrict the results returned by `ll.Sensor` or `ll.SensorRepeat` calls.

**Type:** `number`

**Value:** `0x20`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `DetectType` |
