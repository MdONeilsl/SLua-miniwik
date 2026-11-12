# `table.move`

```lua
table.move(src: {V}, i: number, j: number, d: number, dest: {V}?) -> {V}
```

Copies a contiguous segment from the source array into the destination array, overwriting any existing elements at the destination’s starting position.

## Arguments

| Name | Type | Description |
|---|---|---|
| `src` | `{V}` | Array to copy elements from. |
| `i` | `number` | First index to include in the copy. |
| `j` | `number` | Last index to include in the copy. |
| `d` | `number` | Starting position in destination for the copied elements. |
| `dest` | `{V}?` | Array to receive the copied elements; optional if omitted. |

**Returns:** `{V}`
