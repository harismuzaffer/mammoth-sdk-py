# DataviewPatchOp


## Fields

| Field                            | Type                             | Required                         | Description                      | Example                          |
| -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- |
| `op`                             | *str*                            | :heavy_check_mark:               | Operation                        | {<br/>"value": "replace"<br/>}   |
| `path`                           | *str*                            | :heavy_check_mark:               | Path                             | {<br/>"value": "name"<br/>}      |
| `value`                          | *Optional[Any]*                  | :heavy_minus_sign:               | Patch value                      | {<br/>"value": "New Dataview name"<br/>} |