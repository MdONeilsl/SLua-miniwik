# `ll.GetNextEmail`

```lua
ll.GetNextEmail(address: string, subject: string) -> ()
```

Retrieves the next email from the queue using the email event. To be retrieved, emails must:
1. Be addressed to `{ll.GetKey()}@lsl.secondlife.com`
2. Originate from the specified sender (or any sender if the address is blank)
3. Match the specified subject (or any subject if the subject is blank)

## Arguments

| Name | Type | Description |
|---|---|---|
| `address` | `string` | Sender email address filter, or "" for any address. |
| `subject` | `string` | Email subject filter, or "" for any subject. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `script_communication` |
