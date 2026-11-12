# `ll.GetParcelDetails`

```lua
ll.GetParcelDetails(pos: vector, params: {number}) -> {any}
```

For the parcel located at the specified vector position, this function returns a list of requested details as defined by the params list, with the values returned in the same order they were requested.


## Arguments

| Name | Type | Description |
|---|---|---|
| pos | vector | Position vector in region coordinates (only the X and Y components are used). |
| params | {number} | A list of PARCEL_DETAILS_* flags specifying the attributes to retrieve. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel` |
