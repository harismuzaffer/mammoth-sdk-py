# ConnectionPatchRequest

Subscription detail which needs to be updated


## Fields

| Field                                                                                     | Type                                                                                      | Required                                                                                  | Description                                                                               | Example                                                                                   |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `patch`                                                                                   | List[[models.ConnectionPatchOp](../models/connectionpatchop.md)]                          | :heavy_check_mark:                                                                        | List of patch operations                                                                  | {<br/>"value": [<br/>{<br/>"op": "replace",<br/>"path": "connection",<br/>"value": {<br/>"database": "db"<br/>}<br/>}<br/>]<br/>} |