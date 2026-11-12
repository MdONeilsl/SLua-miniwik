# `ll.TriggerSound`

```lua
ll.TriggerSound(sound: string | uuid, volume: number) -> ()
```

Emits the specified sound once at the given volume, positioned at the object’s current location but not linked to it (remains stationary and cannot be halted or modified). Has no impact on sounds that are attached.


## Arguments

| Name | Type | Description |
|---|---|---|
| `sound` | `string | uuid` | Name of a sound in the prim's inventory, or a UUID. |
| `volume` | `number` | Volume level to set, between 0.0 (silent) and 1.0 (loud). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `sound` |
