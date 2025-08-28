# DataviewPatch

Update dataview properties like rename a dataview, or reset a dataview


## Fields

| Field                                                                                          | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `patch`                                                                                        | List[[models.DataviewPatchOp](../models/dataviewpatchop.md)]                                   | :heavy_check_mark:                                                                             | List of patch operations                                                                       | {<br/>"value": [<br/>{<br/>"value": {<br/>"op": "replace",<br/>"path": "name",<br/>"value": "Renamed Dataview"<br/>}<br/>}<br/>]<br/>} |