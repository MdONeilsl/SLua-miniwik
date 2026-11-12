# `ll.TransferLindenDollars`

```lua
ll.TransferLindenDollars(destination: uuid, amount: number) -> uuid
```

Moves a specified amount of Linden Dollars from the script's owner to the target avatar, necessitating the PERMISSION_DEBIT permission. The function returns a key that can be used to query the outcome of the transaction via the transaction_result event.

## Arguments

| Name | Type | Description |
|---|---|---|
| `destination` | `uuid` | UUID of the destination avatar. |
| `amount` | `number` | Quantity of L$ to transfer (must be greater than 0). |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `money`, `permissions` |
