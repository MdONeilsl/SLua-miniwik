# `ll.SetLinkPrimitiveParams`

```lua
ll.SetLinkPrimitiveParams(link: number, rules: list) -> ()
```

Use ll.SetLinkPrimitiveParamsFast instead. Applies primitive parameters to the specified linked primitive based on the provided rules.

## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `rules` | `list` | A list of PRIM_* rules and data to apply. |

**Returns:** `()`

## Deprecated

- **use:** ll.SetLinkPrimitiveParamsFast

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.2` |
| `categories` | `linkset`, `prim_appearance`, `prim_properties` |
