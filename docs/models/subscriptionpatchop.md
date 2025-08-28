# SubscriptionPatchOp


## Fields

| Field                               | Type                                | Required                            | Description                         | Example                             |
| ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- |
| `op`                                | *Literal["replace"]*                | :heavy_check_mark:                  | Operation                           | {<br/>"value": "replace"<br/>}      |
| `path`                              | *Literal["subscription_id"]*        | :heavy_check_mark:                  | Path                                | {<br/>"value": "subscription_id"<br/>} |
| `value`                             | *str*                               | :heavy_check_mark:                  | Value to replace the attribute with | {<br/>"value": "SubscriptionId"<br/>} |