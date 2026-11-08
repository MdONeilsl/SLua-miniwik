# `bit32.replace`

```lua
bit32.replace(dst: number, src: number, field: number, width: number?) -> number
```

Replaces a segment of bits within the destination value using corresponding bits from the source value. The replacement starts at the specified bit index and spans a given width; an error is raised if this range falls outside 0 to 31.

## Arguments

| Name | Type | Description |
|---|---|---|
| `dst` | `number` | The number whose bits will be overwritten. |
| `src` | `number` | The value supplying the new bit pattern. |
| `field` | `number` | Zero-indexed position where replacement begins. |
| `width` | `number?` | How many bits are being replaced; defaults to one. |

**Returns:** `number`