# `ll.TargetedEmail`

```lua
ll.TargetedEmail(target: number, subject: string, msg: string) -> ()
```

Sends an email with the specified subject and message body to the designated target, which may refer to the object's owner or its root creator. The email is dispatched from `{ll.GetKey()}@lsl.secondlife.com`.

## Arguments

| Name | Type | Description |
|---|---|---|
| `target` | `number` | Target constant (e.g., TARGETED_EMAIL_OBJECT_OWNER or TARGETED_EMAIL_ROOT_CREATOR). |
| `subject` | `string` | Subject of the email. |
| `msg` | `string` | Email message body. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `20.0` |
| `categories` | `avatar_communication` |
