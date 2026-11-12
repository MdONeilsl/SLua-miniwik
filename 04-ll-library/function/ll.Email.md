# `ll.Email`

```lua
ll.Email(address: string, subject: string, msg: string) -> ()
```

Sends an email to the specified address with the provided subject and message content. The email originates from `{ll.GetKey()}@lsl.secondlife.com` and is intended for use in script-based communication; consult ll.GetNextEmail() for retrieving sent messages.


## Arguments

| Name | Type | Description |
|---|---|---|
| `address` | `string` | Destination email address. |
| `subject` | `string` | Subject of the email. |
| `msg` | `string` | Message body of the email. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `20.0` |
| `categories` | `avatar_communication`, `script_communication` |
