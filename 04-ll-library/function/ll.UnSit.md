# `ll.UnSit`

```lua
ll.UnSit(id: uuid) -> ()
```

Causes the agent identified by id to rise from a seated position if they are sitting on the object that hosts this script, or if they are positioned over land controlled by the object's owner.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | UUID of the avatar to unsit. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `sit` |