# `ll.UpdateKeyValue`

```lua
ll.UpdateKeyValue(k: string, v: string, checked: boolean | number, original_value: string) -> uuid
```

Initiates an asynchronous operation to modify the key `k` to the new value `v` within the experience datastore. When `checked` is set to TRUE, the operation will return XP_ERROR_RETRY_UPDATE if the current value does not match `original_value`.


## Arguments

| Name | Type | Description |
|---|---|---|
| `k` | `string` | Key of the key-value pair to update. |
| `v` | `string` | New value for the key-value pair. |
| `checked` | `boolean | number` | Boolean. If TRUE, requires the existing value to match original_value to complete the update; if FALSE, creates the key if needed. |
| `original_value` | `string` | String value to compare against the existing value in the datastore. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `data_storage`, `dataserver`, `experience`, `experience_data` |