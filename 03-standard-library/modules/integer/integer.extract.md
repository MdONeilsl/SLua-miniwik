# `integer.extract`

```lua
integer.extract(src: integer, field: integer, width: integer?) -> integer
```

Retrieves a specified quantity of bits from an integer source, starting at a given index. An error is raised if the requested segment falls outside the valid bit range of 0 through 63.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `integer` | The integer value from which bits will be extracted. |
| `field` | `integer` | The initial position of the bits to retrieve, starting at zero. |
| `width` | `integer?` | Specifies how many bits are needed; defaults to one if not provided. |

**Returns:** `integer`
