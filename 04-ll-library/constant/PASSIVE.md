# `PASSIVE`

This constant is used to identify in-world objects that are static or do not move and thus do not require active server resources. When returned by ll.DetectedType(), it signifies a non-physical object. Additionally, when utilized within filters for ll.Sensor() or ll.SensorRepeat(), it targets physical objects that are inactive, non-moving, non-scripted, or non-physical.

**Type:** `number`

**Value:** `0x4`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `DetectType` |
