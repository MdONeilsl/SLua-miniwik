# `ll.GiveMoney`

```lua
ll.GiveMoney(destination: uuid, amount: number) -> number
```

Moves the specified amount of Linden dollars from the script’s owner to the target avatar. If the PERMISSION_DEBIT permission is not granted, the operation fails silently. The function returns 0; use ll.TransferLindenDollars to associate this transaction with transaction_result events.


## Arguments

| Name | Type | Description |
|---|---|---|
| `destination` | `uuid` | UUID of the destination avatar. |
| `amount` | `number` | Number of L$ to transfer (must be greater than 0). |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `money`, `permissions` |
