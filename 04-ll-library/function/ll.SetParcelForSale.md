# `ll.SetParcelForSale`

```lua
ll.SetParcelForSale(ForSale: boolean | number, Options: list) -> number
```

Configures the sale status of the parcel beneath the object. When ForSale is set to TRUE, it initiates a sale using the specified Options (such as price, designated buyer, and included objects); when ForSale is FALSE, it cancels the sale. This function demands ownership of the parcel and the PERMISSION_PRIVILEGED_LAND_ACCESS permission. Execution results in an error code or 0 upon success.

## Arguments

| Name | Type | Description |
|---|---|---|
| `ForSale` | `boolean | number` | Boolean. If TRUE, puts the parcel up for sale; if FALSE, removes it from sale. |
| `Options` | `list` | A list of options to configure the sale (e.g., price, authorized buyer, and object inclusion). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `parcel` |
