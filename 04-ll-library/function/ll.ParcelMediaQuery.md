# `ll.ParcelMediaQuery`

```lua
ll.ParcelMediaQuery(query: {number}) -> {any}
```

Retrieves media properties of the parcel hosting the script, returning values in the sequence specified by the query parameter. This function is only functional if the object is either owned by the landowner or granted to the land’s group.

## Arguments

| Name | Type | Description |
|---|---|---|
| `query` | `{number}` | A list of PARCEL_MEDIA_COMMAND_* attributes to query. |

**Returns:** `{any}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `2.0` |
| `categories` | `media`, `parcel`, `parcel_media` |
