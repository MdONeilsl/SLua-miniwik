# `ll.GetAgentList`

```lua
ll.GetAgentList(scope: number, options: list) -> {uuid}
```

Retrieves UUID keys of avatars present in the region, filtered according to the specified scope. The result is either a list of UUIDs or a list with an error message string.

## Arguments

| Name | Type | Description |
|---|---|---|
| `scope` | `number` | Scope flag (AGENT_LIST_PARCEL, AGENT_LIST_PARCEL_OWNER, or AGENT_LIST_REGION) to filter the returned agents. |
| `options` | `list` | A list of options to apply (currently unused). |

**Returns:** `{uuid}`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `0.0` |
| `categories` | `avatar`, `parcel`, `region` |
