# `ll.GetLinkPrimitiveParams`

```lua
ll.GetLinkPrimitiveParams(link: number, params: {number}) -> {any}
```

Retrieves a list of primitive parameters specified by the params list for the linked primitive identified by link, behaving identically to ll.GetPrimitiveParams.


## Arguments

| Name | Type | Description |
|---|---|---|
| link | number | Link number (1 for root, >1 for children) or a LINK_* flag to retrieve parameters from. |
| params | {number} | A list of PRIM_* flags specifying the attributes to retrieve. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `linkset`, `prim_appearance` |
