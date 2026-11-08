# `ll.GetVisualParams`

```lua
ll.GetVisualParams(agentid: uuid, params: {number | string}) -> {number | ""}
```

For the specified agent, this function retrieves and returns a list of values corresponding to the visual parameters listed in the params argument.


## Arguments

| Name | Type | Description |
|---|---|---|
| `agentid` | uuid | UUID of the avatar in the same region. |
| `params` | {number | string} | A list of visual parameter IDs or names to retrieve values for. |

**Returns:** `{number | ""}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar` |