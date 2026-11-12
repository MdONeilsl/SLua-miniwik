# `transaction_result`

```lua
transaction_result(id: uuid, success: number, data: string) -> ()
```

This event fires once an asynchronous Linden Dollar transfer is completed. It provides the transaction ID, whether the operation succeeded, and either detailed information or an error message.

## Arguments

| Name | Type | Description |
|---|---|---|
| `id` | `uuid` | The unique identifier key from the transfer call. |
| `success` | `number` | Indicates if the currency exchange was successful or not. |
| `data` | `string` | Transaction details (CSV) or the specific error message. |

**Returns:** `()`
