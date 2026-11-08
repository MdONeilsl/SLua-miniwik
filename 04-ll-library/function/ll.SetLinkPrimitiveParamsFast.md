# `ll.SetLinkPrimitiveParamsFast`

```lua
ll.SetLinkPrimitiveParamsFast(link: number, rules: list) -> ()
```

Applies primitive parameters to the specified linked primitive using the provided rules, without introducing any automatic script sleep delay.


## Arguments

| Name | Type | Description |
|---|---|---|
| `link` | `number` | Link number (1 for root, >1 for children) or a LINK_* flag. |
| `rules` | `list` | A list of PRIM_* rules and data to apply. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance`, `prim_properties` |