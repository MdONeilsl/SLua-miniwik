# `ll.SetTextureAnim`

```lua
ll.SetTextureAnim(mode: number, face: number, sizex: number, sizey: number, start: number, length: number, rate: number) -> ()
```

Configures texture animation on a specified prim face by adjusting scale and offset parameters. The mode parameter controls animation behavior, sizex and sizey specify frame dimensions, start indicates initial frame or angle, length sets the animation duration, and rate determines playback speed in frames per second (or radians per second for ROTATE, UV coordinates per second for SMOOTH).

## Arguments

| Name | Type | Description |
|---|---|---|
| `mode` | `number` | Bitfield of texture animation mode flags (ANIM_ON, LOOP, etc.). |
| `face` | `number` | Face number or ALL_SIDES. |
| `sizex` | `number` | Number of horizontal frames (ignored for ROTATE and SCALE). |
| `sizey` | `number` | Number of vertical frames (ignored for ROTATE and SCALE). |
| `start` | `number` | Start frame number (or radians for ROTATE). |
| `length` | `number` | Number of frames to display (or radians for ROTATE). |
| `rate` | `number` | Playback rate in frames per second (or radians/sec for ROTATE, UV coords/sec for SMOOTH). Must not be zero. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `effects`, `prim`, `prim_appearance` |