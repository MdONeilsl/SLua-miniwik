# `PRIM_MEDIA_FIRST_CLICK_INTERACT`

This boolean value controls the behavior when a user clicks an unfocused media face that is currently playing: if set to TRUE, the click will behave exactly like one on a focused media face and will subsequently forward the click event to the web browser. If set to FALSE, the media prim will be focused, ensuring that any future clicks are routed to the web browser instead. Note that viewer settings have an influence on this flag; however, it is functional by default for most prims.

**Type:** `number`

**Value:** `8`

## Definition fields

| Field | Value |
|---|---|
| `categories` | `PrimMediaParam` |
