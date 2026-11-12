# `ll.RequestSimulatorData`

```lua
ll.RequestSimulatorData(region: string, data: number) -> uuid
```

Initiates an asynchronous request for specific simulator data (specified via a DATA_SIM_* constant) related to the given region, which dispatches a dataserver event and yields a key handle for tracking the query.


## Arguments

| Name | Type | Description |
|---|---|---|
| `region` | `string` | Case-sensitive region name. |
| `data` | `number` | DATA_SIM_* flag of the requested simulator data. |

**Returns:** `uuid`

## Definition fields

| Field | Value |
|---|---|
| `energy` | `10.0` |
| `sleep` | `1.0` |
| `categories` | `dataserver`, `region` |
