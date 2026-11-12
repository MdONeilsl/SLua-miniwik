# `ll.SetLinkTextureAnim`

```lua
ll.SetLinkTextureAnim(link: number, mode: number, face: number, sizex: number, sizey: number, start: number, length: number, rate: number) -> ()
```

Configures texture animation on a specified face of a linked prim by adjusting scale and offset based on the animation mode. The sizex and sizey parameters specify the number of animation frames, start indicates the initial frame or angle, length sets the animation duration, and rate controls playback speed in frames per second (or radians per second for ROTATE, UV coordinates per second for SMOOTH).

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag to animate. |
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
| `categories` | `effects`, `linkset`, `prim_appearance` |
