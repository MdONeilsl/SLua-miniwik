# `ll.ExecCharacterCmd`

```lua
ll.ExecCharacterCmd(command: number, options: list) -> ()
```

Transmits a command defined by the `command` parameter to the pathing system, along with any associated options. At present, this function is limited to halting pathfinding or initiating a jump for the character.

## Arguments

| Name | Type | Description |
|---|---|---|
| `command` | `number` | Pathfinding command to execute. |
| `options` | `list` | A list of options for the command (e.g., jump height for CHARACTER_CMD_JUMP). |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `pathfinding` |