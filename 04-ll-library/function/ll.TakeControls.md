# `ll.TakeControls`

```lua
ll.TakeControls(controls: number, accept: boolean | number, pass_on: boolean | number) -> ()
```

Captures input events—such as keyboard and mouse actions—from the agent, targeting only those defined by the controls parameter. The accept flag controls whether these events trigger script callbacks, while pass_on dictates whether the inputs still execute their standard behaviors. This function necessitates the PERMISSION_TAKE_CONTROLS runtime permission.

## Arguments

| Name | Type | Description |
|---|---|---|
| `controls` | `number` | Bitfield of CONTROL_* flags to intercept. |
| `accept` | `boolean | number` | Boolean. Determines whether control events are generated to trigger script handlers. |
| `pass_on` | `boolean | number` | Boolean. If TRUE, the keys also perform their default functions; if FALSE, default actions are suppressed. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `input`, `permissions` |
