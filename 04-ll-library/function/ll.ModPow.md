# `ll.ModPow`

```lua
ll.ModPow(a: number, b: number, c: number) -> number
```

Computes the value of base raised to the exponent, then takes the result modulo modulus (equivalent to (b^e) % m). Input values are coerced to the unsigned 32-bit range [0..4294967295]. The output is converted to the signed 32-bit range [-2147483648..2147483647]. This operation is guaranteed not to overflow, in contrast to direct computation of (b^e), which may result in infinity due to overflow.

## Arguments

| Name | Type | Description |
|---|---|---|
| `a` | `number` | 32-bit unsigned integer base. |
| `b` | `number` | 32-bit unsigned integer exponent. |
| `c` | `number` | 32-bit unsigned integer modulus. |

**Returns:** `number`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `math` |