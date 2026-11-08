# `ll.DetectedRot`

```lua
ll.DetectedRot(number: number) -> quaternion
```

Given a detection index, this function retrieves the corresponding rotation value; if the index is invalid, it returns the default rotation <0.0, 0.0, 0.0, 1.0>.

## Arguments

| Name | Type | Description |
|---|---|---|
| number | number | Index of the detection information. |

**Returns:** `quaternion`

## Definition fields

| Field | Value |
|---|---|
| energy | 10.0 |
| sleep | 0.0 |
| categories | detected |