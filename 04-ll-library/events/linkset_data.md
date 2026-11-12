# `linkset_data`

```lua
linkset_data(action: number, name: string, value: string) -> ()
```

When any script modifies the linked set's stored data via `ll.LinksetData*`, this event fires across all scripts. The handler receives the specific operation performed, the name of the modified setting, and its new content.

## Arguments

| Name | Type | Description |
|---|---|---|
| `action` | `number` | The operation performed, such as updating, deleting, or resetting data. |
| `name` | `string` | The identifier for the changed key, or a list if multiple keys were affected. |
| `value` | `string` | The current string content associated with the setting (may be empty if deleted). |

**Returns:** `()`
