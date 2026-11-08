# `ll.SetPayPrice`

```lua
ll.SetPayPrice(price: number, quick_pay_buttons: {number}) -> ()
```

This function sets the default price displayed in the payment text field and defines the four quick-pay button values for the payment dialog.


## Arguments

| Name | Type | Description |
|---|---|---|
| `price` | `number` | Default price integer shown in the text field (can accept PAY_* constants or positive values). |
| `quick_pay_buttons` | `{number}` | A list of four integer values or PAY_* constants specifying the button payment choices. |

**Returns:** `()`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `money`, `prim_properties`, `user_interface` |