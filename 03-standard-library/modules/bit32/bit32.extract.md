# `bit32.extract`

```lua
bit32.extract(src: number, field: number, width: number?) -> number
```

This function pulls a specified count of bits from the source integer (`src`), beginning at the index given by `field`. An error will occur if this defined bit range falls outside 0 to 31.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `number` | The integer value that will be processed. |
| `field` | `number` | Starting position of the bits to retrieve (0 being the lowest). |
| `width` | `number?` | How many bits should be extracted; defaults to one if left out. |

**Returns:** `number`
