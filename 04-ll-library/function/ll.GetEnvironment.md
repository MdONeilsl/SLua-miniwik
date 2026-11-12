# `ll.GetEnvironment`

```lua
ll.GetEnvironment(pos: vector, params: {number}) -> {any}
```

Returns a list of the current environment parameters for the parcel or region located at pos, with values fetched in the sequence defined by the params list.

## Arguments

| Name | Type | Description |
|---|---|---|
| `pos` | `vector` | Position vector in region coordinates (X/Y determine the parcel, or region if X/Y are -1; Z determines the sky track altitude). |
| `params` | `{number}` | A list of environmental attributes to retrieve. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel`, `parcel_appearance` |
