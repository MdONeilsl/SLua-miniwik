# `integer.replace`

```lua
integer.replace(dst: integer, src: integer, field: integer, width: integer?) -> integer
```

Replaces a contiguous bit range in `dst` using bits from `src`, starting at bit position `field` and extending `width` bits (or 1 bit if `width` is omitted). Fails if the replacement range exceeds bit indices 0–63.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dst` | `integer` | Target integer whose bits will be modified. |
| `src` | `integer` | Source integer providing the bits to insert. |
| `field` | `integer` | Zero-based index marking the start of the bit replacement. |
| `width` | `integer?` | Bit count to replace; defaults to 1 if not provided. |

**Returns:** `integer`
